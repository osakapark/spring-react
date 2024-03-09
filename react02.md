# 2.React-Router
## 2.1 설치
* npm install react-router-dom

## 2.2
App.js 수정 43  page

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
const { createBrowserRouter } = require("react-router-dom");
const Loading = <div>Loading....</div>
const Main = lazy(() => import("../pages/MainPage"))
const root = createBrowserRouter([
    {
        path: "",
        element: <Suspense fallback={Loading}><Main /></Suspense>
    }
])
export default root;
```

```javascript
//BasicLayout.js
const BasicLayout = ({ children }) => {
    return (
        <>
            <header className="bg-teal-400 p-5">
                <h1 className="text-2xl md:text-4xl">Header</h1>
            </header>
            <div className="bg-white my-5 w-full flex flex-col space-y-4 md:flex-row md:space-x-4 md:space-y-0">
                <main className="bg-sky-300 md:w-2/3 lg:w-3/4 px-5 py-40">
                    {children}
                </main>
                <aside className="bg-green-300 md:w-1/3 lg:w-1/4 px-5 py-40">
                    <h1 className="text-2xl md:text-4xl"> Sidebar </h1>
                </aside>
            </div>
        </>
    );
}
export default BasicLayout;
```

index.js 
> App.js 
>> root.js
>>> /pages/todo/IndexPage 
>>>> BasicLayout 
>>>>> BasicMEnu

>>>> TEST
