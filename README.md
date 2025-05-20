# **BLOG App (API_Routing)**
![screenShort](https://github.com/mukeshvommu318/Featching_and_Routing_Part-3-NXT-/blob/49e7b57e8eba7006837a36a12b1be20ea5219559/Screenshot%20(5).png)

## Learnings
### ->  **Featching Data from API and Modifying the Data (Changing snake_case to camelCase)**

**code**

        state = { isLoading: true, blogsData: [] }

      componentDidMount() {
        this.getBlogsData()
      }

      getBlogsData = async () => {
        const response = await fetch('https://apis.ccbp.in/blogs')
        const statusCode = await response.statusCode
        console.log(statusCode)
        const data = await response.json()

    const formattedData = data.map(eachItem => ({
      id: eachItem.id,
      title: eachItem.title,
      imageUrl: eachItem.image_url,
      avatarUrl: eachItem.avatar_url,
      author: eachItem.author,
      topic: eachItem.topic,
    }))
    this.setState({ blogsData: formattedData, isLoading: false })
      }


### -> **Adding Link to each item in the List**

**<code>**

    return (
    <Link to={`/blogs/${id}`} className="item-link">
      <div className="item-container">
        <img className="item-image" src={imageUrl} alt={`item${id}`} />
        <div className="item-info">
          <p className="item-topic">{topic}</p>
          <p className="item-title">{title}</p>
          <div className="author-info">
            <img className="avatar" src={avatarUrl} alt={`avatar${id}`} />
            <p className="author-name">{author}</p>
          </div>
        </div>
      </div>
    </Link>
      )

**<app.js>**

    <BrowserRouter>
    <Header />
    <Switch>
      <Route exact path="/" component={BlogsList} />
      <Route path="/about" component={About} />
      <Route path="/contact" component={Contact} />
      <Route path="/blogs/:id" component={BlogItemDetails} />
      <Route component={NotFound} />
    </Switch>
    </BrowserRouter>

-> When user clicks on the Blog the path gets updates (eg: if user clicks on 3rd blog **(path : localhost:3000/blogs/:3 )** 

    <Route path="/blogs/1" component={BlogItemDetails} />
    <Route path="/blogs/2" component={BlogItemDetails} />
    <Route path="/blogs/3" component={BlogItemDetails} />
    **<Route path="/blogs/:id" component={BlogItemDetails} />**  

-> Here Route will pass additional props (match, History, Location) to the BlogItemDetails
**match** 
It is an Object That contain the information about the path from which the component is rendered
Q) What to access the id inside the match
A) Inside match -> params object -> id 

**code**

    componentDidMount() {
    this.getBlogItemData()
      }
    getBlogItemData = async () => {
    const { match } = this.props
    const { params } = match
    const { id } = params

    const response = await fetch(`https://apis.ccbp.in/blogs/${id}`)
    const data = await response.json()

    const updatedData = {
      title: data.title,
      imageUrl: data.image_url,
      content: data.content,
      avatarUrl: data.avatar_url,
      author: data.author,
    }
    this.setState({ blogData: updatedData, isLoading: false })
  }

  

# **How to Deploy React Js Application into the GitHub** 
## Step 1: Create the GitHub repository
## Step 2: After Creating Repository Follow this Steps
    git init

    git add .

    git commit -m "first commit"

    git branch -M main
    
##  Step 3: Enter the following command in which we have to replace the <username> with the username of your GitHub account and the <rep Name> with the name of the repository which you have created.
    git remote add origin https://github.com/<username>/<rep Name>.git

## Enter the following commands which will push the react application to the above repository
    git push -u origin main

## Step 4 Adding the GitHub Pages dependency packages
    npm install gh-pages --save-dev

## Step 5 Adding the properties to the package.json file
    "homepage": "https://<Username>.github.io/<Repository-name>"
    
    "scripts":{
    "predeploy": "npm run build",
    "deploy": "gh-pages -d build" 
    } 

## Step 6 Pushing the code updates to the GitHub repository and finally deploying the application
    git add .
    git commit -m "commit"
    git push

    npm run deploy

