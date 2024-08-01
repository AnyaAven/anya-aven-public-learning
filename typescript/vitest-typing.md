# Vitest Typing

```json
{
  "compilerOptions": {
    "types": ["@testing-library/jest-dom"]
  }
}
```

To have extended types for `expect` function from `vitest` and `react-testing-library`
we needed to configure our TS config file.
This allowed my editor to have known about extended expect functionality,
`toHaveClass()` and
`toHaveTextContent()`.

```ts
expect(alertElement).toHaveClass('alert-success');
expect(alertElement).toHaveTextContent('Success message');
```

### Reference
https://stackoverflow.com/questions/57861187/property-tobeinthedocument-does-not-exist-on-type-matchersany