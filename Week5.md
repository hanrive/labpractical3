# What is ArcGIS Enterprise?

* "ArcGIS Enterprise is the foundational software system for GIS, powering mapping and visualization, analytics, and data management. It is the backbone for running the Esri suite of applications and your own custom applications... Collaboration and flexibility are central to ArcGIS Enterprise, allowing you to organize and share your work on any device, anywhere, at any time. ArcGIS Enterprise gives you complete control over your deployment."*

## Communicate what the purpose of AGE is to a company or organization


## Understand components of the base deployment (minimum required)


## Learn how to manage an implementation of the base deployment (by completing this checklist)


## Learn what components add-on to AGE (ArcGIS Enterprise)

# What is ArcGIS Server?

*"ArcGIS Server is the software that powers all 2D data and spatial capabilities in Esri's web-based products. At the core, ArcGIS Server creates and shares map services, which are made available through a URL using a REST interface (aka endpoint).  ArcGIS Server used to be a stand-alone and complete product, but in 2016 Esri split it up and requires separate licenses for publishing functionality in Server, like image (raster) services for sharing aerial imagery."*

### https://smartbear.com/learn/performance-monitoring/api-endpoints/
- API = Application Programming Interface
- Allows two systems to communicate with one another

  > Alright, imagine you have a magical toy box, and you're a child who wants to play with your toys. But instead of reaching inside the box yourself, you have a friend, let's call them Mr. API, who can get the toys for you.
  >
  > Now, Mr. API works like a magical messenger between you and the toy box. You tell Mr. API what toy you want to play with, and he goes to the toy box, gets it for you, and brings it back. You don't need to worry about how he gets it; you just need to ask.
  > 
  > In this way, an API (which stands for "Application Programming Interface") is like a friendly helper that lets different computer programs talk to each other and share information. It's like a special language they use to communicate and exchange data, just like you and Mr. API communicate to get your toys. So, you can think of an API as a way for different programs to work together and share what they have, just like friends sharing toys from a toy box.

- API are categorized as either SOAP or REST and both are used to access web services
  - SOAP relies solely on XML to provide messaging services while REST offers a more lightweight method usingURLs in most cases to receive or send information
  - REST uses four different HTTP 1.1 verbs to perform tasks: **GET, POST, PUT,** and **DELETE**
- An API Endpoint is one end of a communication channel as in when an API interacts with another system the touchpoints of this communication are considered endpoints
  - These are important because they ensure that each touchpoint in API communication is intact in transferring vital information, processes, transactions, and more (API performance relies on its ability to communicate effectively with API Endpoints)
 
### https://enterprise.arcgis.com/en/server/latest/get-started/windows/what-is-arcgis-for-server-.htm
- ArcGIS Server is a back-end server software component of ArcGIS Enterprise that makes your geographic information available to others in your organization and, optionally, anyone with an internet connection. This is accomplished through GIS services, which allow a server computer to receive and process requests for information sent by other devices.
- There are two ways ArcGIS Server can be used:
  - The primary way is as part of an ArcGIS Enterprise organization in which ArcGIS Server is federated (meaning it integrates the security and sharing models of your portal with one or more ArcGIS Server sites) with an ArcGIS Enterprise portal
    - Way most users should use
    - This pattern means your geo data is made available through layers and web maps in the organization that can then be used in a variety of apps with little to no custom development required
  - The second way is as a stand-alone pattern in which ArcGIS Server is not federated with an ArcGIS Enterprise portal
    - Common in previous releases
    - Stand-alone sites commonly use ArcGIS Server to provide foundational content and services as a data provider with little to no security controls on the services which allows users to provide their own apps to interact with the content
   
### https://enterprise.arcgis.com/en/server/latest/get-started/windows/what-s-included-with-arcgis-server.htm
As soon as you install ArcGIS Server you can publish web services from your GIS resources such as maps, imagery, and geoprocessing models. There are a variety of preconfigured services that help you perform common tasks such as: *Caching tools, GeoAnalytics tools, Geocoding tools, Printing tools, Publishing tools, etc.*

- ArcGIS Server Manager:
  - Application used to work with your server from which you can add and remove services, tune and secure your services, and organize services in folders
- ArcGIS Web Adaptor:
  - Is an optional setup that you can install to allow ArcGIS Server to work with your web server for reasons such as wanting to customize the URL and port number or configuring security polices at the web tier
- ArcGIS Server Services Directory:
  - Tool that uses representational state transfer (REST) technology to help you discover information about your services and the corresponding URLs you can use for development
  - Can also be used to allow your server to be discovered through browsing or searches
    - For example: through the Services Directory, users of your server can access a geographic footprint of all available services and can also retrieve service-level metadata about your services and preview them in a web browser/ArcGIS Earth/Google Earth
- REST API and command line utilities for server administration:
  - Allows you to script common server administration tasks such as adding a machine to a site, publishing a service, adding permissions, and so on
  - The ArcGIS Server Administration Directory provides interactive access to this API which is helpful for learning the hierarchy of commands and constructing HTTP requests to put in your scripts

# Understand how to navigate the REST Services Directory API

*At the main interface of ArcGIS Server (AGS) is the REST API to interact with data and map services using a URL. The AGS REST Endpoint can be "navigated" using a friendly HTML website, or an Application-friendly JSON interface. Irrespective of how you use the ArcGIS REST API (JSON or HTML), to master AGS you must understand how to construct a URL to manipulate and retrieve spatial and non-spatial data. All resources and operations exposed by the ArcGIS Services portion of the REST API are accessible through a hierarchy of endpoints for each GIS service published with AGS or a Federated ArcGIS Portal (and ArcGIS Online). Remember: ArcGIS Enterprise is just a bundle of software, which ArcGIS Server is one component.*

### https://developers.arcgis.com/rest/services-reference/enterprise/get-started-with-the-services-directory.htm
The ArcGIS Server Services Directory is a RESTful representation of all the services running on an ArcGIS Server site. Every instance of ArcGIS Server includes the Services Directory as part of its installation. While the Services Directory will work out of the box, once ArcGIS Server has been fully installed the Edit Services Directory operation can be used to modify aspects of the Services Directory, such as disabling the HTML view of the directory and modifying URLs to applications such as Map Viewer that can be accessed to view a published web map.

- The Services Directory utilizes the RESTful architectural style that allows the API to reveal a hierarchy of information about itself through endpoints and when you use the Services Directory you can choose to navigate through the directory from its HTML view using links or manually construct specific endpoint URLs

##### Construct the well-known endpoint
The well-known endpoint is the site root from which the rest of the API can be accessed. For ArcGIS Enterprise, the default version of the well-known endpoint is as follows: https:// < host > / < context > /rest/services **(WITHOUT SPACES)**
- < host > **(WITHOUT SPACES)** has three parts to its structure:
  - The name of the ArcGIS Server host organization or the web adapter host
  - The domain
  - The top-level domain (.com)
- < context > **(WITHOUT SPACES)** = either the name of the web adaptor configured for ArcGIS Server (specified during the installation) or the site name (arcgis) if no web adapter is associated with your deployment of ArcGIS Server
- rest/services = the directory endpoint -> appending this to the well-known endpoint URL provides access to the site root, allowing you to see any top-level operations, services, and folders

With the site root URL structure in place, you can choose to either use the HTML view of the directory to navigate the site or continue to modify the URL manually to access specific endpoints. This example shows the additional elements that can be added to the site root URL to navigate to a service, service layer, a resource, or perform an action: https:// < host >/< context >/rest/services/< folderName >/< serviceName >/< ServiceType >/< layer >/< resource >/< operation >?< parameter=value > **(WITHOUT SPACES)**
- < folderName > **(WITHOUT SPACES)** = the name of the folder that holds specific services
  - case sensitive
- < serviceName >/< ServiceType> **(WITHOUT SPACES)** = the name-type pair for a specific service
  - case sensitive
  - an example of a service accessible from the site root would not include < folderName > however a service in a specific folder would include it
- < layer> **(WITHOUT SPACES)** = the numerical representation of a service layer
- < resource > **(WITHOUT SPACES)** = the name of an associated resource endpoint for either a service or service layer
- < operation > **(WITHOUT SPACES)** = the name of an operation that can be performed on a specific service, service layer, or a resource associated with a service or service layer
- ? = the beginning of the parameterlist
- < parameter=value > **(WITHOUT SPACES)** = the parameters and their associated input for an operation
  - the parameters of a request are in the form of name-value pairs
  - the values themselves may be literal (name=value) for simple parameter, or JSON representations (name={< json-object >}) **(WITHOUT SPACES)** for more complex structres

- The most common request method when using the Services Directory is a GET request created from an operation form in the HTML view of the directory

## Demonstrating how to navigate the Read REST Services Directory, Read MapServer and Read FeatureServer types to provide one or more (a collection of) Read dynamic layers, using one of those Read Layers within the collection, and the most important part, how to use the Read Query method on the layer itself to interrogate the data (similar to a SELECT statement in SQL).

### Navigating the REST Services Directory:

### MapServer:

### FeatureServer:

### Dynamic layers:

### Layers:

### Query:
