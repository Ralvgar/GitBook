# useState\(\)

You can use params of your url route to pass info to other components of your app with useState.



```text
<Route path="/unexpected-error/:id" component={UnexpectedError} />

const UnexpectedError = () => {

const { id } = useParams();

 return (
        <div>
            <button className='btn btn-dark'><Link to={`/${id}`} className='search-link'> Return </Link> </button>
        </div>
    )
```

