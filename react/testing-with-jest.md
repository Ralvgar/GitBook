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



## TDD

It is a design process. It’s a robust way of designing software components interactively, one unit at a time, by making sure that the individual component’s behavior is specified through unit tests beforehand.

![](../.gitbook/assets/image%20%289%29.png)

1. Before you write implementation code, write some code that proves that the implementation works or fails. Watch the test fail before moving to the next step \(this is how we know that a passing test is not a false positive — how we test our tests\).
2. Write the implementation code and watch the test pass.
3. Refactor if needed. You should feel confident refactoring your code now that you have a test to tell you if you’ve broken something.

### Why TDD?

In TDD, we write only a few lines of code each time to pass a failing unit test. So, our development cycle is very short, which makes debugging very easy too. Also it makes other developers’ lives easier by being able to understand how your feature should work.



{% embed url="https://jestjs.io/" %}





