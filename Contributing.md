Hi, welcome to hic et nunc repository. We're happy you're here.

We're trying to optimize the source code little by little, and it is only fair to write some notes on the thinking behind why we're making some of the decisions we're making. Writing this down will help you (the contributor) get comfortable with the source code.

## Testing

We're currently implementing [Storybook](https://storybook.js.org/) which will be the ideal place where you can check how the components look. We're also currently implementing basic unit testing using [Jest](https://jestjs.io/).

## Components

When creating a component you need to provide a few properties in order to render the component properly. Try to avoid creating prop drilling, or even accessing react context in a component. The components should be as dumb as possible. The only place where you should have access to API requests, or React.Context is at the page level (`src/pages/*`).

In terms of standard its a good practice to first do global imports, then relative imports and finally scss imports. So a component would look something like this:

```jsx
import React from 'react' // a global import
import { Button } from '../button' // a relative import
import styles from './index.module.scss' // a sass import

export const MyComponent = () => {
  return <div className={styles.container}>My Component</div>
}
```

There are some auxiliary components that aren't doing much besides aiding with the layout. A good example of that is the `/src/pages/objkt-display` where you have `<Container/>` and `<Padding />`. These components are similar to what `reactstrap` provides, but we're trying to minimize our bundle size, so we're reducing on dependencies.

## PR

Pull requests should be as small as possible. At the moment there are a lot of eslint errors everywhere, and instead of fixing them all in one go (potentially breaking something and not being able to identify exactly what broke it), we're deciding to go page by page, component by component, fixing those warnings, removing unused code, etc.

Because it's been a very small team contributing to this project, we've been mainly contributing directly into the `main` branch, but that won't happen anymore.

We will be using a Git flow approach. This means that you will need to create a feature branch from the `develop` branch, write all your code there, and then when you submit your PR you submit it against the `develop` branch. Once the features on `develop` are tested and ready to push to production, an Admin will create a PR from `develop` to `main` and kick off a deployment.

If Git flow is something new to you, don't feel intimidated, come and join us on Discord and we'll take the time to help.

# How to Contribute to the Wiki?
You can clone this repo if you'd like,

`git clone https://github.com/hicetnunc2000/hicetnunc.wiki.git`

however, since wikis do not have pull requests, you should make a new issue and put a label as "FAQ". Someone who is already contributor will review it and merge your changes. There is also a [template](https://github.com/hicetnunc2000/hicetnunc/blob/main/.github/ISSUE_TEMPLATE/faq_update.md)