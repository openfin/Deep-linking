# Deep-linking

## Overview
Deep Linking utilizes a custom protocol handler to invoke an application if not already running and pass context to a specific location within an OpenFin application via a uniform resource identifier (URI). This enables application providers the ability to deep link an OpenFin application from anywhere that can invoke a “link” like a browser, email client or another OpenFin application.

## Usage
In order to leverage the Deep Linking feature in your application you must use the “args” object in fin.desktop.main for processing added parameters on launch and the “args” object on the run-requested application event if your application is already running.

Runtime 8.56.24.41+ required
RVM 3.7.1+ required

### Example Deep Link:
`fins://mydomain.com/path-to-manifest/app.json?$$parameter1=value1&$$paramater2=value2`

### Example usage of fin.desktop.main and run-requested:
// On application launch parameters are passed through
`fin.desktop.main(function(args) 
    {
    //args parameter contains deep link context
     console.log(args.parameter1);
})`

// If app is already running parameters are passed through the “run-requested” event

`app.addEventListener("run-requested", 
    function (event) {
        if(event.userAppConfigArgs){`
//args parameter contains deep link context
console.log(event.userAppConfigArgs.parameter1);
