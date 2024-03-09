# 2.React-Router
## 2.1 설치
* npm install react-router-dom

## 2.2  구조

>index.js 
>> App.js 
>>> root.js
>>>> /pages/todo/IndexPage 
>>>>> BasicLayout 
>>>>>> BasicMenu

>>>>> /pages/todo/ListPage (children)


```javascript
//App.js
import { RouterProvider } from "react-router-dom";
import root from "./router/root";
function App() {
    return (
        <RouterProvider router={root}></RouterProvider>
    );
}
export default App;
```


```javascript
//root.js
import { Suspense, lazy } from "react";
import todoRouter from "./todoRouter";
const { createBrowserRouter } = require("react-router-dom");
const Loading = <div>Loading....</div>
const Main = lazy(() => import("../pages/MainPage"))
const About = lazy(() => import("../pages/AboutPage"))
const TodoIndex = lazy(() => import("../pages/todo/IndexPage"))

const root = createBrowserRouter([
    {
        path: "",
        element: <Suspense fallback={Loading}><Main /></Suspense>
    },
    {
        path: "about",
        element: <Suspense fallback={Loading}><About /></Suspense>
    },
    {
        path: "todo",
        element: <Suspense fallback={Loading}><TodoIndex /></Suspense>,
        children: todoRouter()
        
    }
])
export default root;
```

```javascript
//BasicLayout.js
import BasicMenu from "../components/menus/BasicMenu";
const BasicLayout = ({ children }) => {
    return (
        <>
            {/* 기존 헤더 대신 BasicMenu*/}
            <BasicMenu />
            {/* 상단 여백 my-5 제거 */}
            <div className="bg-white my-5 w-full flex flex-col space-y-1 md:flex-row md:space-x-1 md:space-y0">
                {/* 상단 여백 py-40 변경 flex 제거 */}
                <main className="bg-sky-300 md:w-2/3 lg:w-3/4 px-5 py-5">{children}</main>
                {/* 상단 여백 py-40 제거 flex 제거 */}
                <aside className="bg-green-300 md:w-1/3 lg:w-1/4 px-5 flex py-5">
                    <h1 className="text-2xl md:text-4xl">Sidebar</h1>
                </aside>
            </div>
        </>
    );
}
export default BasicLayout;
```

```javascript
//Menu.js
import { Link } from "react-router-dom";
const BasicMenu = () => {
    return (
        <nav id='navbar' className=" flex bg-blue-300">
            <div className="w-4/5 bg-gray-500" >
                <ul className="flex p-4 text-white font-bold">
                    <li className="pr-6 text-2xl">
                        <Link to={'/'}>Main</Link>
                    </li>
                    <li className="pr-6 text-2xl">
                        <Link to={'/about'}>About</Link>
                    </li>
                    <li className="pr-6 text-2xl"><Link to={'/todo/'}>Todo</Link></li>
                </ul>
            </div>
            <div className="w-1/5 flex justify-end bg-orange-300 p-4 font-medium">
                <div className="text-white text-sm m-1 rounded" >Login</div>
            </div>
        </nav>
    );
}
```
```javascript
//ListPage.js
import { useSearchParams } from "react-router-dom";
const ListPage = () => {
    const [queryParams] = useSearchParams()
    const page = queryParams.get("page") ? parseInt(queryParams.get("page")) : 1
    const size = queryParams.get("size") ? parseInt(queryParams.get("size")) : 10
    return (
        <div className="p-4 w-full bg-white">
            <div className="text-3xl font-extrabold">
                Todo List Page Component {page} --- {size}
            </div>
        </div>
    );
}
export default ListPage;
```
