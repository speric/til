Given a React component that accepts a boolean prop, the proper way to set that prop to `true` is:

```jsx
<MyComponent
  someProp
/>
```

and not:

```jsx
<MyComponent
  someProp={true}
/>
```

I'd made the mistake, when encountering the [jsx-boolean-value](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/jsx-boolean-value.md) rule violation of doing `someProp={true}`, of removing the prop declaration altogether, misreading the intention of the rule. This caused much weeping, because at that point I was at the mercy of the underlying component's defaults. In this case the default for `someProp` was `false`, and my code was not behaving as expected.

So, TIL: the proper way to address the `jsx-boolean-value` warning!
