# Leak report

The reason why Valgrind intitially has a problem is because there is a calloc in the strip() method that is never freed after
it's used in a different function which checks whether or not a string is "clean". The way you would fix it is using free()
when it's done being used in the is_clean() function, which is what I've done, as it should have (theoretically) no effect on the
result. Valgrind declares that there is no more memory leak at all now that's it's been freed.
