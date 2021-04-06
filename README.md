# react-help
<i>diagrams, references or useful  links<i/>


## hook flow/lifecycle diagram

https://github.com/donavon/hook-flow


## useEffect with async functions:

```
React.useEffect(() => {
  doSomeAsyncThing().then(result => {
    console.log(result)
    // do something with the result
  })
})
```

usually SoMe AySynC thing would be an api call like so:

```
React.useEffect(() => {
    if (pokemonName === '') {
      return
    } else {
      // this resets the result to show the loading/no pokemon value after consecutive searches
      setState({
        status: 'idle',
        pokemon: null,
        error: null,
      });

      fetchPokemon(pokemonName)
        .then(pokemonData => {
          setState(
            {
              status: 'resolved',
              pokemon: pokemonData,
              error: null
            }
          )
        })
        .catch(error => setState(
          {
            status: 'rejected',
            pokemon: null,
            error: error,
          }
        )
      )
    }
  }, [pokemonName])
  ```
  
  with the fetchPokemon being an api call to a graphQL/REST endpoint.
