# Deep-linking

## Overview
Deep Linking utilizes a custom protocol handler to invoke an application if not already running and pass context to a specific location within an OpenFin application via a uniform resource identifier (URI). This enables application providers the ability to deep link an OpenFin application from anywhere that can invoke a “link” like a browser, email client or another OpenFin application.

## Usage
In order to leverage the Deep Linking feature in your application can retrieve the search string using standard web practices for processing added parameters on launch and the “args” object on the run-requested application event if your application is already running.

Runtime 8.56.24.41+ required
RVM 3.7.1+ required

### Example Deep Link:
```javascript
fins://mydomain.com/path-to-manifest/app.json?$$parameter1=value1&$$paramater2=value2
```

### Example usage of fin.desktop.main and run-requested:
```javascript
// On application launch parameters are passed through to the main window
fin.desktop.main(userAppConfigArgs => {
    console.log(userAppConfigArgs);
    // { parameter1: 'value1', parameter2: 'value2' }
}

// If app is already running parameters are passed through the “run-requested” event
app.addEventListener("run-requested", function (event) {
    if(event.userAppConfigArgs){
        //args parameter contains deep link context
        console.log(event.userAppConfigArgs.parameter1);
    }
})
```
## License
MIT

The code in this repository is covered by the included license.

However, if you run this code, it may call on the OpenFin RVM or OpenFin Runtime, which are covered by OpenFin’s Developer, Community, and Enterprise licenses. You can learn more about OpenFin licensing at the links listed below or just email us at support@openfin.co with questions.

https://openfin.co/developer-agreement/ <br/>
https://openfin.co/licensing/

## Support
Please enter an issue in the repo for any questions or problems. Alternatively, please contact us at support@openfin.co
