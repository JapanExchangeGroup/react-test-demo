# start testing 

```
./testing.sh
```

# sample output

```
 PASS  src/Link.test.js
 PASS  src/App.test.js

Test Suites: 2 passed, 2 total
Tests:       2 passed, 2 total
Snapshots:   3 passed, 3 total
Time:        1.078 s
Ran all test suites.

Watch Usage: Press w to show more.
```

# Test Link.js

```js
import React from 'react';
import renderer, { act } from 'react-test-renderer';
import Link from './Link';

test('Link changes the class when hovered', () => {
  const component = renderer.create(
    <Link page="http://www.facebook.com">Facebook</Link>,
  );
  let tree = component.toJSON();
  expect(tree).toMatchSnapshot();

  act(() => {
    // manually trigger the callback
    tree.props.onMouseEnter();  
  });
  
  // re-rendering
  tree = component.toJSON();
  expect(tree).toMatchSnapshot();

  act(() => {
    // manually trigger the callback
    tree.props.onMouseLeave();
  });
  
  // re-rendering
  tree = component.toJSON();
  expect(tree).toMatchSnapshot();
});
```

