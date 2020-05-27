# assignmet
this is to complete assignment of week 3
##these functions are written to complete the assignment of week 3 of R Progrramming.
##github: DhwaniPandya222

##the function creats special "matrix" object that can cache its inverse.

makeCacheMatrix <- function(x = matrix()){        ## argument with "matrix"
  inv <- NULL                                     ## initialize inv as NULL
  set <- function(y) {                            ## define the set function                      
  x <<- y                                         ## value of matrix
  inv <<- NULL                                    ## if new matrix got than reser inv to NULL
}
get <- function() x                               ## define get function
setinverse <- function(inverse) inv <<- inverse   ## assign value of inv
getinverse <- function() inv                      ## gets the value of inv where called
list(set = set,get = get,setinverse = setinverse, ##have to follow order to functions with $ operator.
     getinverse = getinverse)   
}


##the functions compute inverse of special "matrix" returned by makeCacheMatrix above.
##if the inverse has already been calculate (and matrix has not changed ), then cacheSolve will retrieve the inverse from the cache.

cacheSolve <- function(x, ...){
                              ##Return a matrix that is the inverse of "x"
 inv <- x$getinverse()
 if(!is.null(inv)) {
   message("getting cached data")
   return(inv)
 }
 data <- x$get()
 inv <- solve(data, ...)
 x$setinverse(inv)
 inv
}
