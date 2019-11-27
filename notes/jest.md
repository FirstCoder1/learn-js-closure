## Jest handy notes

### Testing a promise

There are several ways to do it 
1. using async [tutorial/docs](https://jestjs.io/docs/en/tutorial-async)
2.If the below `exectCallBack` is not used, then the frame work will not wait for results, but goes till the end and test passes. To Ensure we go in this flow, we use the callback
```js
  describe('when something', () => {
    it('that has assertion inside the result of an promise', (exectCallBack) => {
          let promise = callMethodThatReturnsPromise();
          return promise.then(value => {
            expect(value).toBeDefined();
            exectCallBack(); // This will ensure, this is executed
        });
    });
  });
```

If you just want to see if a promise is resolved or failed, then do this.
```js
  describe('when something', () => {
    it('that has assertion inside the result of an promise', (exectCallBack) => {
          let promise = callMethodThatReturnsPromise();
          return promise;
        });
    });
  });
```