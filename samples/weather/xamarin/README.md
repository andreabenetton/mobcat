# WeatherTron 9000
WeatherTron 9000 is a weather app sample that showcases best patterns and practices for building, testing, and deploying mobile apps using [Xamarin](https://visualstudio.microsoft.com/xamarin/), [Azure DevOps](https://azure.microsoft.com/en-us/solutions/devops/), and [AppCenter](https://appcenter.ms/)

(Add Screenshots)

## Backend
The sample also comes with a [web service backend build with asp.net core](https://github.com/xamarin/mobcat/tree/dev/samples/weather/azure) which you can host to run the app. Deployment instructions can be found [here](https://github.com/xamarin/mobcat/blob/dev/samples/weather/azure/README.md)

## Solution Overview
The solution consists of the following projects:
- MobCAT: The MobCAT library which contains useful services and pattern base classes
- MobCAT.Forms: The MobCAT Forms library which contains useful Forms base classes, services, behaviors, and converters
- Weather: The Weather Forms project which contains the XAML and shared code
- Weather.Android: The Weather Android specific project contains Android assets
- Weather.iOS: The Weather iOS specific project contains iOS assets
- Weather.UITests: The UI Test project
- Weather.UnitTests: The unit test project which uses mock services using [Moq](https://github.com/moq/moq4)

## MVVM
The app uses the [MVVM(Model-View-ViewModel)](https://docs.microsoft.com/en-us/xamarin/xamarin-forms/enterprise-application-patterns/mvvm) pattern to decouple business logic & presentation code. MVVM utility classes can be found in MobCAT/MVVM

## Service Container
The MobCAT library also includes a service container to register & consume services within the app. This enables registering platform specific services and consuming them through a common interface within shared code. It also enables mock services to be registered for UI test or unit test purposes.

## Bootstrap
Weather.Bootstrap.cs is where the app services are instantiated and registered in the ServiceContainer. Platform specific startup actions can also be invoked using the provided parameter in the Begin method.
The Begin method is called from the AppDelegate for iOS, and MainActivity for Android respectively.

## Custom Weather Font
The custom weather icons are from https://erikflowers.github.io/weather-icons/

## App Secrets
The app secrets in Weather are protected using [mobcat_client_secrets](https://github.com/xamarin/mobcat/tree/master/mobcat_client_secrets) to prevent secret keys from being committed into source code. 