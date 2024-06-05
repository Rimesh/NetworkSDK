# NetworkSDK

NetworkSDK is a simple networking library for iOS applications. It provides a set of protocols and structures to simplify network operations, such as GET, PATCH, POST, and DELETE requests.

## Features

- Perform network requests with ease using a protocol-based approach.
- Supports GET, PATCH, POST and DELETE HTTP methods.
- Provides an `Endpoint` structure to define API endpoints.
- Utilizes Combine framework for handling asynchronous operations.

## Installation

To use NetworkSDK in your project, copy the NetworkSDK.xcframework into your Xcode project or add it as a package dependency using Swift Package Manager.

## Usage

### NetworkManagerProtocol

The `NetworkManagerProtocol` defines the core methods for performing network requests. Here’s a quick overview of its methods:

```swift
public protocol NetworkManagerProtocol: AnyObject {
    var decoder: JSONDecoder { get set }

    func get<T>(type: T.Type, endPoint: Endpoint) -> AnyPublisher<T, NetworkError> where T: Decodable

    func patch(endPoint: Endpoint) -> AnyPublisher<Bool, NetworkError>
    func patch<T>(type: T.Type, endPoint: Endpoint) -> AnyPublisher<T, NetworkError> where T: Decodable

    func post(endPoint: Endpoint) -> AnyPublisher<Bool, NetworkError>
    func post<T>(type: T.Type, endPoint: Endpoint) -> AnyPublisher<T, NetworkError> where T: Decodable

    func delete(endPoint: Endpoint) -> AnyPublisher<Bool, NetworkError>
}
```

### Endpoint

The Endpoint struct is used to define the properties of an API endpoint.

```swift
public struct Endpoint {
    let path: String
    let method: HTTPMethod
    let authorization: AuthorizationType
    var queryItems: [URLQueryItem]
    var bodyParams: [String: String]
    var headers: [String: String]
}
```
