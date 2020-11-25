# JSX

 JSX is a syntax extension to JavaScript. It is similar to a HTML language, but it has full power of JavaScript. JSX gets compiled to `React.createElement()` calls which return plain JavaScript objects called “React elements”.

```jsx
const Proyect = () => {

    return (
        <div className='row mx-5 pt-5 mt-3'>
            <p className='about__header mb-1'>Proyect</p>
            <ul className='list-unstyled mt-0'>
                <li>
                    <a className='about__anchor' href='https://mallorcaboot.camp/' rel="noreferrer" target="_blank">
                        Mallorca Bootcamp
                    </a>
                </li>
            </ul>
        </div>
    )
}
```



