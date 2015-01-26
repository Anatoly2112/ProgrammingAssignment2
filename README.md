## ProgrammingAssignment2
makeCacheMatrix <- function(x = matrix()) {

      m <- NULL
      set <- function(y) {
        x <<- y
        m <<- NULL
      }
      get <- function() x
      setinv <- function(solve) m <<- solve
      getinv <- function() m
      list(set = set, get = get,
           setinv = setinv,
           getinv = getinv)
  
}

cacheSolve <- function(x, ...) {
      ptm <- proc.time()
      m <- x$getinv()             
      if(!is.null(m)) {
        message("getting cached data")
        cat("Process Time", proc.time() - ptm)
        return(m)
      }
      mydata <- x$get()
      m <- solve(mydata, ...)
      x$setinv(m)
      cat("Process Time", proc.time() - ptm)
      m
      
  
}
