# React Service Worker

Simple and powerful alternative for the default create-react-app registerServiceWorker

## Installation

    npm install react-service-worker -S

## Usage

the default `registerServiceWorker` generated by `create-react-app` is very simple and only gives you ways to register and unregister your service worker. Any other action should be implemented manually.

The `react-service-worker` module provides better organization and more features like listen for updates on your APP easily.

The integration is very simple, just open the `src/index` file in your project and replace

    import registerServiceWorker from './registerServiceWorker';

for:

    import registerServiceWorker from 'react-service-worker';

and done! This way, the react service worker will act just like the default registerServiceWorker.

An better use of this module would be:

    const appSW = registerServiceWorker()

    ReactDOM.render(<App appServiceWorker={appSW} />, document.getElementById('root'));

and in the App component you could do this to show messages such as "the app has been installed" or "there is an new update, please refresh":

    componentDidMount() {
        const { appServiceWorker } = this.props
        appServiceWorker.onInstalled(() => this.setState({ showInstalledMessage: true }))
        appServiceWorker.onUpdateFound(() => this.setState({ showUpdateMessage: true }))
    }

## Tests

  `npm test`
