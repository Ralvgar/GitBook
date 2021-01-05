# Testing with Jest

 Jest is a JavaScript testing framework maintained by Facebook with a focus on simplicity and support for large web applications. It works with projects using Babel, TypeScript, Node.js, React, Angular, Vue.js and Svelte.

### Why Do We Need to Test Our Application?

Test our app will make your process more agile. It helps us with future changes as code that has been already implemented can be touched with confidence. In case our changes would likely cause a bug, it won’t reach production but will break our unit tests. This means that the quality of our code will increase as our test suite will catch bugs earlier, before making it to the end-user.

This also means the cost of bug fixing will be reduced, as you know where to look and why your application breaks.

Example from my [tree-component](https://github.com/Ralvgar/tree-component) project:

```javascript
describe("Screen tests", () => {
  it('renders the first level elements', () => {
    const { getByText } = render(<TreeComponent file={treeFile} />);
    getByText("First");
    getByText("Second");
    getByText("Third");
  });

  it('shouldn\'t render second level elements', () => {
    const { queryByText } = render(<TreeComponent file={treeFile} />);
    expect(queryByText("First-First")).toBeNull();
  });

  it('should change to default icon when passing through no prop', () => {
    render(<TreeComponent file={treeFile} />);
    expect(document.querySelector('.fa-caret-right')).toBeInTheDocument();
  });

  it('should change to plus icon when passing through a prop', () => {
    render(<TreeComponent file={treeFile} iconStyle={"plus"} />);
    expect(document.querySelector('.fa-plus')).toBeInTheDocument();
  });

  it('should change to angle icon when passing through a prop', () => {
    render(<TreeComponent file={treeFile} iconStyle={"angle"} />);
    expect(document.querySelector('.fa-angle-right')).toBeInTheDocument();
  });

  it('should change to folder icon when passing through a prop', () => {
    render(<TreeComponent file={treeFile} iconStyle={"folder"} />);
    expect(document.querySelector('.fa-folder')).toBeInTheDocument();
  });

  it('shouldn\'t have changed the icon before clicked', () => {
    render(<TreeComponent file={treeFile} />);
    expect(document.querySelector('.fa-caret-down')).toBeNull();
  });

  it('should change the icon when clicked', () => {
    render(<TreeComponent file={treeFile} />);
    expect(document.querySelector('.fa-caret-right')).toBeInTheDocument();
    expect(document.querySelector('.fa-caret-down')).toBeNull();
    screen.getByText("First").click();
    expect(document.querySelector('.fa-caret-down')).toBeInTheDocument();
  });
});


describe("Functions tests", () => {
  it('should return the icon value for FontAwesome', () => {
    expect(getIconFromIconName("plus")).toStrictEqual([faMinus, faPlus]);
    expect(getIconFromIconName("angle")).toStrictEqual([faAngleDown, faAngleRight]);
    expect(getIconFromIconName("folder")).toStrictEqual([faFolderOpen, faFolder]);
    expect(getIconFromIconName("")).toStrictEqual([faCaretDown, faCaretRight]);
  });

})
```

{% embed url="https://jestjs.io/" %}





