<script>
  import {
    Router,
    Route,
    Link,
    createHistory,
    createMemorySource,
  } from "../../../src";
  import UseFocus from "./UseFocus.svelte";
  import UseFocusAsync from "./UseFocusAsync.svelte";

  const memoryHistory = createHistory(createMemorySource());
</script>

<Router history={memoryHistory}>
  <Link data-testid="a11y-link-a" to="a">Link A</Link>
  <Link data-testid="a11y-link-b" to="b">Link B</Link>
  <Link data-testid="a11y-link-c" to="b/c">Link C</Link>
  <Link data-testid="a11y-link-d" to="b/d">Link D</Link>
  <Link data-testid="a11y-link-e" to="b/e">Link E</Link>

  <Route path="a">
    <h1 data-testid="a11y-route-a">Path A</h1>
    <p>
      Lorem, ipsum dolor sit amet consectetur adipisicing elit. Laborum, quas?
    </p>
  </Route>

  <Route path="b/*">
    <Route path="/">
      <h1 data-testid="a11y-route-b">Path B</h1>
      <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Laborum, quas?
      </p>
    </Route>

    <Route path="c">
      <h2 data-testid="a11y-route-c">Path C</h2>
      <p>
        Lorem, ipsum dolor sit amet consectetur adipisicing elit. Laborum, quas?
      </p>
    </Route>

    <Route path="d">
      <UseFocus />
    </Route>

    <Route path="e">
      <UseFocusAsync />
    </Route>
  </Route>
</Router>
