# Netflix_Clone
## This is the site for seeing the Originanal movies , the trending movies and the Top rated one

The netflix original movies

![image](https://user-images.githubusercontent.com/103323625/185897857-cd4b94be-d4ef-429c-852c-57249dbc6f55.png)


The treding movies and the Top rated 

![image](https://user-images.githubusercontent.com/103323625/185898382-be10d65f-52ff-449f-89ff-31fa15c06521.png)
### Link
https://endearing-belekoy-11721a.netlify.app

### code

``` javascript


// Call the main functions the page is loaded
window.onload = () => {
    getOriginals()
    getTrendingNow()
    getTopRated()
  }
  
  // ** Helper function that makes dynamic API calls **
  function fetchMovies(url, dom_element, path_type) {
    // Use Fetch with the url passed down 
    fetch(url)
    .then(response => {
      if (response.ok) {
        return response.json()
      } else {
        throw new Error('something went wrong')
      }
    })
    // Within Fetch get the response and call showMovies() with the data , dom_element, and path type
    .then(data => {
        showMovies(data, dom_element, path_type)
      })
      .catch(error_data => {
        console.log(error_data)
      })
}
  
  //  ** Function that displays the movies to the DOM **
  showMovies = (movies, dom_element, path_type) => {
    
    // Create a variable that grabs id or class
    var moviesEl = document.querySelector(dom_element)
  
    // Loop through object
    for (var movie of movies.results) {
  
      // Within loop create an img element
      var imageElement = document.createElement('img')
  
      // Set attribute
      imageElement.setAttribute('data-id', movie.id) 
  
      // Set source
      imageElement.src = `https://image.tmdb.org/t/p/original${movie[path_type]}`
  
      // Add event listener to handleMovieSelection() onClick
      imageElement.addEventListener('click', e => {
        handleMovieSelection(e)
      })
    
      // Append the imageElement to the dom_element selected
      moviesEl.appendChild(imageElement)
    }
  
}

```

