- Following this Youtube [tutorial](https://www.youtube.com/watch?v=vCOSTG10Y4o) by Lama Dev.
- This is a Github flavored Markdown file.
- Note based on NextJS14

#### NextJS Specific Helpful Components

- Link
  - Advantage is, it fetches pages on the background before we click the link. @ [26:30](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=26:30)
  - You can disable prefetching if there a performance issue.
- Images
  - Images @ [59:37](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=59:37)
  - Advantages, NextJS automatically optimizes images based on screen size.
    - Sample of optimization @ [1:01:56](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=1:01:56)
  - Instead of specifying width and height directly on the Image component, you can encapsulate it within a div element that has defined dimensions and should be position `relative` and the Image tag should have the prop `fill` @ [1:02:49](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=1:02:49).  
  - Adding **external images**
    - Sample @ [1:04:58](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=1:04:58)
  - **My thoughts:** For assets hosted locally or inside public folder, Use import  for add image source and create an alias for public folder (inside ts config). Based from experience manually adding path to public will break on NextJS apps hosted on sub folders

- More on Font and Images optimization (built-in advantages)
  - Read [here](https://nextjs.org/learn/dashboard-app/optimizing-fonts-images).

- Partial rendering
  - Please refer to docs
  - Related to Root Layout and Partial 
  
- Links
 - Automatic code-splitting and prefeteching
 - NextJS automatically code splits by route segments (mentioned Chapter 5 Tutorial) - Traditional React SPA, where
 - if Link is visible on view port it will be prefetched
 - splitting code by route means if a route has error, other route will still work




### Quick Basics
- Listed below are some terms and concept that we need to know.
#### App Router

- Easily create routes
- Routing based on` /app` or `src/app` folder structure. It can be a nest of folders.
- Can pass dynamic parameters e.g., `details/[id]` or `details/[slug]`

#### Pages

- page.tsx
- Each folder must have a `page.tsx` file, this will be used on the routing.

#### Layouts

- layout.tsx
- If the folder have a `layout.tsx` file, it will be used as the layout for the page.
- If no layout.tsx on folder it will use its nearest parent.
- Sample Layout @ [23:00](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=23:00)

#### Group Routing

- Group Routing @ [17:54](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=17:54)
- folder name should have parenthesis e.g., (auth)
- Group names is **not considered as part of the route** e.g., `(auth)/login` will be accessed in the url as `/login`.

#### Loading Indicator

- Loading @ [28:18](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=28:18)
- You can throttle down on the network to see the loading.

#### Error layout

- Error Layout @ [29:23](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=29:23)
- Must be a client component.

#### 404 - Customizing the default

- Custom 404 @ [31:00](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=31:00)
- The default 4040 can be overridden by creating a `not-found.tsx` under app.

#### Rendering Strategy (Server Side and Client Side Renderings)
- Start @  [1:35:45](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=1:35:45)
- Showing PROS and CONS @ [1:52:07](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=1:52:07)
- We can combine Server side and Client side component
- Server Side Rendering @ [1:56:10](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=1:56:10)
  - Server returns the minimal HTML and CSS to the  browser 
    - PROS: 
      - faster load times, since it only sends the minimal files (on first load abd hydration begins)
      - SEO friendly since tags like H1 is  rendered
    - CONS
      - Not yet interactive on first ms
      - More server load
      - State Management
- Client Side rendering
  - Bundles all out files for the website
  - Returns empty HTML (not SEO friendly)
  - Initial load is slower.

#### Server Components
- This is the default of NexJS
- Advantages: 
  - Runs on server, therefore can be pre rendered
- Assingment: What are Server components advantage
#### Client Components
- Activated when using directive "use client"
- Is when you want to use hooks, interactivity events like onClick
- The initial render is still on the server

#### Hydration Error
- Start @ [1:58:50](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=1:58:50)
- To prevent this: [3 ways]
    - use, useEffect hooks - so any update on the state is only done on client component or create sa useState flag.
    - Disable server side rendering on client component by using `dynamic imports` with `ssr false`.
    - Create a div enclosing the dynamic component(that caused the error) with property suppressHydrationWarning prop

#### Question: Wrapping Server side component with Client Side component
- Start @ [2:04:56](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=2:04:56).
- Like wrapping ContextProvider
- I will still be a server side component.


### Date Fetching and Caching
- Start @ [2:17:50](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=2:17:50)
- By default caches the fetch respons and can be disabled passing options the fetch or you can also revalidate date duration
- parans and searchParams

#### Suspense
- Example of creating a suspense block @ [2:29:22](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=2:29:22)

### SEO
- Adding static custom metadata inside the taget page.tsx
- Creating a static template @  [3:03:12](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=3:03:12)
- Create dynamic title and description using generateMetaData @ [3:04:21](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=3:04:21)

### Server Actions
- Starts @  [3:05:57](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=3:05:57)
- In the network tab you can see it as a  POST request
- **My thoughts:**
  - Server Actions is the new to go
  - If you can use server action use it. (There might be advantages in Route Handlers)
  - In Route Handler there is boiler plate (create folder structure)

### Server Actions vs Router Handler (formerly API routes)
- https://vercel.com/blog/common-mistakes-with-the-next-js-app-router-and-how-to-fix-them
- Starts @ [3:19:43](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=3:19:43)
- **My thoughts:**
  - If you want expose an use an API/Route Handler (a fullstack NExtJS app)
### Styling

- Styling Intro @ [32:00](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=32:30)
- CSS modules @ [38:48](https://www.youtube.com/watch?v=vCOSTG10Y4o&t=38:48)
- My thoughts: It might be better to use Tailwind in my opinion and I skipped the whole styling part of the video.


