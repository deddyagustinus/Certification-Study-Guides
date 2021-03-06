# Developing ASP.NET MVC Web Applications (70-486)

This guide is based, in large part, on the skills summary lists located here:

- [Microsoft Learning Portal](https://www.microsoft.com/en-us/learning/exam-70-486.aspx "https://www.microsoft.com/en-us/learning/exam-70-486.aspx")
- [Microsoft Born To Learn](https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=486 "https://borntolearn.mslearn.net/certification/p/wiki?es=webApp&ec=486") Training and Certification Community Wiki site

Anything else listed additionally is based on my own observations. Links listed here may be subject to copyright protection and access to such is up to the discretion of the authors\owners to which they pertain.

####Caveats

1. This exam targets MVC 5.1 and VS2013. A number of aspects of MVC 4 still apply, as well as the general functionality of MVC on ASP.Net, but be aware of the MVC 5.x distinctions and how VS2013 is expected to be utilized.
2. Where the guide mentions "Implement", be prepared to know common method and parameter usage involved with said technology or namespace.
3. There is a good portion of this test involving Azure services and the functionality thereof.


####Additional Resources

- [PluralSight "Learning Path"](https://www.pluralsight.com/blog/software-development/asp-net-mvc-microsoft-exam-70-486 "https://www.pluralsight.com/blog/software-development/asp-net-mvc-microsoft-exam-70-486") for 70-486
- Being familiar with the [SOLID principles](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design) "https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)") of OO programming and design will likely help with the material covered here
- [Failed The Turing Test](http://failedturing.blogspot.com/search/label/70-486 "http://failedturing.blogspot.com/search/label/70-486")
- Barbarian Meets Coding - [Notes for 70-486](https://www.barbarianmeetscoding.com/wiki/asp-net-mvc/asp-net-mvc-certification/ "https://www.barbarianmeetscoding.com/wiki/asp-net-mvc/asp-net-mvc-certification/") (Outstanding reference)
	- Additionally, for HTML/CSS and Javascript/jQuery info, refer to Jaime's [70-480 guide](https://www.barbarianmeetscoding.com/blog/2015/03/15/on-how-i-passed-the-70-480-certification-exam/ "https://www.barbarianmeetscoding.com/blog/2015/03/15/on-how-i-passed-the-70-480-certification-exam/")
- Adnan Massod R&D - [Study Notes for 70-486](http://blog.adnanmasood.com/2013/05/20/study-notes-for-70-486-developing-asp-net-mvc-4-web-applications/ "http://blog.adnanmasood.com/2013/05/20/study-notes-for-70-486-developing-asp-net-mvc-4-web-applications/")

##Design the application architecture (15-20%)

###Plan the application layers

- Plan data access
	- [Data Access Practices Using Microsoft .Net: A Nerdly Comparison](https://msdn.microsoft.com/en-us/data/ff707264.aspx "https://msdn.microsoft.com/en-us/data/ff707264.aspx")
	- Based on the exam ref prep book, you have a choice between using:
		- an ORM (Object/Relational Mapper):
			1. [Entity Framework](http://msdn.microsoft.com/en-us/data/ef.aspx "http://msdn.microsoft.com/en-us/data/ef.aspx")
			2. [NHibernate](http://nhibernate.info/ "http://nhibernate.info/")
			3. [Linq-to-SQL](https://msdn.microsoft.com/en-us/library/bb425822.aspx "https://msdn.microsoft.com/en-us/library/bb425822.aspx")
		- Roll your own DAL (using [ADO.Net](https://msdn.microsoft.com/en-us/library/e80y5yhx(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/e80y5yhx(v=vs.110).aspx"), etc.)
	- [EFMVC – ASP.NET MVC 4, Entity Framework 5 Code First and Windows Azure (Demo App)](http://efmvc.codeplex.com/ "http://efmvc.codeplex.com/")
	- Understand the difference between Database-First and Code-First design strategies
		- Data annotations for code first ([validation](http://labs.bjfocus.co.uk/2014/03/validation-attributes-in-code-first/ "http://labs.bjfocus.co.uk/2014/03/validation-attributes-in-code-first/") and [database related](http://labs.bjfocus.co.uk/2014/03/database-related-attributes-in-code-first/ "http://labs.bjfocus.co.uk/2014/03/database-related-attributes-in-code-first/"))
	- Understand and implement the [Repository Pattern](https://codeteddy.com/2013/09/03/learning-mvc-part-5repository-pattern-in-mvc3-application-with-entity-framework/ "https://codeteddy.com/2013/09/03/learning-mvc-part-5repository-pattern-in-mvc3-application-with-entity-framework/")
- plan for separation of concerns
	- [Wikipedia definition](https://en.wikipedia.org/wiki/Separation_of_concerns "https://en.wikipedia.org/wiki/Separation_of_concerns")
	- [Intro the MVC architecture and SoC](http://www.c-sharpcorner.com/UploadFile/1492b1/introduction-to-mvc-architecture-and-separation-of-concerns/ "http://www.c-sharpcorner.com/UploadFile/1492b1/introduction-to-mvc-architecture-and-separation-of-concerns/")
- appropriate use of [MVC components](https://msdn.microsoft.com/en-us/library/dd381412(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/dd381412(v=vs.110).aspx"):
	- [models](http://www.asp.net/mvc/overview/getting-started/introduction/adding-a-model "http://www.asp.net/mvc/overview/getting-started/introduction/adding-a-model"), 
	- [views](http://www.asp.net/mvc/overview/getting-started/introduction/adding-a-view "http://www.asp.net/mvc/overview/getting-started/introduction/adding-a-view"), 
	- [controllers](http://www.asp.net/mvc/overview/getting-started/introduction/adding-a-controller "http://www.asp.net/mvc/overview/getting-started/introduction/adding-a-controller") 
- choose between [client-side and server side](http://programmers.stackexchange.com/questions/138561/pros-cons-between-emphasizing-client-side-or-server-side-processing "http://programmers.stackexchange.com/questions/138561/pros-cons-between-emphasizing-client-side-or-server-side-processing") processing; 
- design for scalability 
	- via [async request handling](http://blog.stevensanderson.com/2008/04/05/improve-scalability-in-aspnet-mvc-using-asynchronous-requests/ "http://blog.stevensanderson.com/2008/04/05/improve-scalability-in-aspnet-mvc-using-asynchronous-requests/")
	- for the [Database](http://programmers.stackexchange.com/a/117359 "http://programmers.stackexchange.com/a/117359")

###Design a distributed application

- Design a hybrid application (on-premises versus off-premises, including [Azure](https://msdn.microsoft.com/en-us/library/hh871440.aspx "https://msdn.microsoft.com/en-us/library/hh871440.aspx"))
	- [Cloud Hybrid Application Using Service Bus Relay](http://www.windowsazure.com/en-us/develop/net/tutorials/hybrid-solution/ "http://www.windowsazure.com/en-us/develop/net/tutorials/hybrid-solution/")
		- app.config example:

				<system.serviceModel>
				...
				  <services>
				     <service name="ProductsServer.ProductsService">
				       <endpoint address="sb://yourServiceNamespace.servicebus.windows.net/products" binding="netTcpRelayBinding" contract="ProductsServer.IProducts" behaviorConfiguration="products"/>
				     </service>
				  </services>
				  <behaviors>
				     <endpointBehaviors>
				       <behavior name="products">
				         <transportClientEndpointBehavior>
				            <tokenProvider>
				               <sharedAccessSignature keyName="RootManageSharedAccessKey" key="yourKey" />
				            </tokenProvider>
				         </transportClientEndpointBehavior>
				       </behavior>
				     </endpointBehaviors>
				  </behaviors>
				</system.serviceModel>


		- App implementation example:
		
		
				namespace ProductsWeb.Controllers
				{
				    using System.Linq;
				    using System.ServiceModel;
				    using System.Web.Mvc;
				    using Microsoft.ServiceBus;
				    using Models;
				    using ProductsServer;
				
				    public class HomeController : Controller
				    {
				        // Declare the channel factory.
				        static ChannelFactory<IProductsChannel> channelFactory;
				
				        static HomeController()
				        {
				            // Create shared access signature token credentials for authentication.
				            channelFactory = new ChannelFactory<IProductsChannel>(new NetTcpRelayBinding(),
				                "sb://yourServiceNamespace.servicebus.windows.net/products");
				            channelFactory.Endpoint.Behaviors.Add(new TransportClientEndpointBehavior {
				                TokenProvider = TokenProvider.CreateSharedAccessSignatureTokenProvider(
				                    "RootManageSharedAccessKey", "yourKey") });
				        }
				
				        public ActionResult Index()
				        {
				            using (IProductsChannel channel = channelFactory.CreateChannel())
				            {
				                // Return a view of the products inventory.
				                return this.View(from prod in channel.GetProducts()
				                                 select
				                                     new Product { Id = prod.Id, Name = prod.Name,
				                                         Quantity = prod.Quantity });
				            }
				        }
				    }
				}

	
- plan for [session management](http://msdn.microsoft.com/library/ms178586.aspx "http://msdn.microsoft.com/library/ms178586.aspx") in a distributed environment, 
- plan [web farms](http://weblogs.asp.net/scottgu/introducing-the-microsoft-web-farm-framework "http://weblogs.asp.net/scottgu/introducing-the-microsoft-web-farm-framework")

###*Design and implement the Azure role life cycle

- Identify and implement Start, Run, and Stop events
	-  [Startup Lifecycle of Windows Azure Role](http://blog.syntaxc4.net/post/2011/04/13/Windows-Azure-Role-Startup-Life-Cycle.aspx "http://blog.syntaxc4.net/post/2011/04/13/Windows-Azure-Role-Startup-Life-Cycle.aspx")
- identify startup tasks (IIS configuration [app pool], registry configuration, third-party tools)
	- [How to configure and run startup tasks for a cloud service](https://azure.microsoft.com/en-us/documentation/articles/cloud-services-startup-tasks/ "https://azure.microsoft.com/en-us/documentation/articles/cloud-services-startup-tasks/")

###Configure state management

- Choose a state management mechanism (in-process and out of process state management), 
- plan for scalability, 
- use cookies or local storage to maintain state, 
- apply configuration settings in web.config file, 
- implement sessionless state (for example, QueryString)

#### Resources
- [State Management Recommendations](https://msdn.microsoft.com/en-us/library/z1hkazw7(v=vs.120).aspx "https://msdn.microsoft.com/en-us/library/z1hkazw7(v=vs.120).aspx")

###Design a caching strategy

- Implement [page output caching](http://www.asp.net/mvc/overview/older-versions-1/controllers-and-routing/improving-performance-with-output-caching-cs "http://www.asp.net/mvc/overview/older-versions-1/controllers-and-routing/improving-performance-with-output-caching-cs") (performance oriented)
	- Duration: measured in seconds
	- VaryByParam: "none", "*" (=all), "{param name};..."
	- Location: 
		- Any
		- Client
		- Downstream
		- Server
		- ServerAndClient 
		- None
	- OutputCaching can also be configured via profile (example):
		- app.config


				<caching>
				<outputCacheSettings>
				    <outputCacheProfiles>
				        <add name="Cache1Hour" duration="3600" varyByParam="none"/>
				    </outputCacheProfiles>
				</outputCacheSettings>
				</caching>



		- controller

				using System;
				using System.Web.Mvc;
				
				namespace MvcApplication1.Controllers
				{
				    public class ProfileController : Controller
				    {
				        [OutputCache(CacheProfile="Cache1Hour")]
				        public string Index()
				        {
				            return DateTime.Now.ToString("T");
				        }
				    }
				}



- implement [data caching](https://msdn.microsoft.com/en-us/library/dd997357.aspx "https://msdn.microsoft.com/en-us/library/dd997357.aspx"), 
- implement [HTTP caching](http://betterexplained.com/articles/how-to-optimize-your-site-with-http-caching/ "http://betterexplained.com/articles/how-to-optimize-your-site-with-http-caching/"), 
- implement [Azure caching](https://blogs.msdn.microsoft.com/webdev/2013/11/30/instant-azure-caching-with-mvc/ "https://blogs.msdn.microsoft.com/webdev/2013/11/30/instant-azure-caching-with-mvc/")

###Design and implement a WebSocket strategy

- [Read](https://msdn.microsoft.com/en-us/library/system.net.websockets.websocket.receiveasync(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/system.net.websockets.websocket.receiveasync(v=vs.110).aspx") and [write](https://msdn.microsoft.com/en-us/library/system.net.websockets.websocket.sendasync(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/system.net.websockets.websocket.sendasync(v=vs.110).aspx") string and binary data asynchronously (long-running data transfers), 
- choose a [connection loss strategy](http://failedturing.blogspot.com/2014/11/microsoft-70-486-design-and-implement.html "http://failedturing.blogspot.com/2014/11/microsoft-70-486-design-and-implement.html"), 
- decide a strategy for when to use WebSockets, 
- implement SignalR

###Design HTTP modules and handlers

- Implement synchronous and asynchronous modules and handlers, 
- choose between modules and handlers in IIS (verbatim from Barbarian Meets Coding)
	
----------
**HTTP handlers** allow you to inject logic based on the extension of the file name requested, they are executed based of file extensions, URLs and HTTP verbs. **HTTP modules** are event driven and inject logic before a resource is requested.

Some ways to differentiate when to use which:

- serve requests for specific URL/extensions => *Http handler*
- applies to all requests based on arbitrary rules => *Http module*
- need information available prior to calling to MVC code => *Http module*
- handle specific files differently => *Http handler*

####`HttpHandler` vs `HttpModule` Summary

- `HttpHandler` processes HTTP endpoints requests whereas,
- `HttpModule` gives you access to the HTTP pipeline, which allows it to inspect incoming requests and outgoing responses by subscribing to events.

----------

####Preparation resources

- [Entity Framework Development workflows](http://msdn.microsoft.com/en-US/data/jj590134 "http://msdn.microsoft.com/en-US/data/jj590134")
- [DataAdapters and DataReaders](http://msdn.microsoft.com/en-us/library/ms254931(v=vs.110).aspx "http://msdn.microsoft.com/en-us/library/ms254931(v=vs.110).aspx")
- [ASP.NET State Management overview](http://msdn.microsoft.com/en-us/library/75x4ha6s(v=vs.100).aspx "http://msdn.microsoft.com/en-us/library/75x4ha6s(v=vs.100).aspx")
- [Why use the Entity Framework? Yeah, why exactly?](http://weblogs.asp.net/fbouma/why-use-the-entity-framework-yeah-why-exactly "http://weblogs.asp.net/fbouma/why-use-the-entity-framework-yeah-why-exactly")

##Design the user experience (20-25%)

###Apply the user interface design for a web application

- Create and apply styles by using CSS, 
- structure and lay out the user interface by using HTML
	-  [Sending form data](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms/Sending_and_retrieving_form_data "https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms/Sending_and_retrieving_form_data")
- implement dynamic page content based on a design
	- Canvas: An HTML5 element that works like an `<img>` tag, allowing the display of 2d content dynamically
		- Placing fallback context inside the `<canvas>` tag allows browsers which don't support canvas to still render the static content. Browsers that do support `<canvas>` tags will ingore the internal static content.

###Design and implement UI behavior

- Implement client validation, 
- use JavaScript and the DOM to control application behavior, 
- extend objects by using [prototypal inheritance](http://javascript.info/tutorial/inheritance "http://javascript.info/tutorial/inheritance"), 
- use AJAX to make partial page updates, 
- implement the UI by using JQuery

###Compose the UI layout of an application

- Implement partials for reuse in different areas of the application
	- [`@Html.Partial` vs. `@Html.RenderPartial`](http://stackoverflow.com/a/5248218/885317 "http://stackoverflow.com/a/5248218/885317") 
- design and implement pages by using Razor templates (Razor view engine)
	- [BeginForm](https://msdn.microsoft.com/en-us/library/system.web.mvc.html.formextensions.beginform(v=vs.118).aspx "https://msdn.microsoft.com/en-us/library/system.web.mvc.html.formextensions.beginform(v=vs.118).aspx") 
	- [TextArea](https://msdn.microsoft.com/en-us/library/system.web.mvc.html.textareaextensions.textarea(v=vs.118).aspx "https://msdn.microsoft.com/en-us/library/system.web.mvc.html.textareaextensions.textarea(v=vs.118).aspx")
	- [TextBox](https://dzone.com/articles/aspnet-mvc-html-helpers "https://dzone.com/articles/aspnet-mvc-html-helpers")
- design layouts to provide visual structure, 
- implement master/application pages

###Enhance application behavior and style based on browser feature detection

- Detect browser features and capabilities; 
- create a web application that runs across [multiple browsers and mobile devices](https://www.simple-talk.com/dotnet/asp.net/multiple-views-and-displaymode-providers-in-asp.net-mvc-4/ "https://www.simple-talk.com/dotnet/asp.net/multiple-views-and-displaymode-providers-in-asp.net-mvc-4/")
- enhance application behavior and style by using vendor-specific extensions, for example, CSS
	- browser specific prefix (such as -webkit- or -moz- or -ms-)

###*Plan an adaptive UI layout

- Plan for running applications in browsers on multiple devices (screen resolution, CSS, HTML)
	- [Media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries "https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries")
- plan for mobile web applications

####Preparation resources

- [Build a better mobile browsing experience](http://msdn.microsoft.com/en-us/magazine/hh288079.aspx "http://msdn.microsoft.com/en-us/magazine/hh288079.aspx")
- [Display modes](http://www.asp.net/whitepapers/mvc4-release-notes#_Toc303253810 "http://www.asp.net/whitepapers/mvc4-release-notes#_Toc303253810")
- [Building Modern Web Apps Jump Start](https://mva.microsoft.com/training-courses/building-modern-web-apps-jump-start "https://mva.microsoft.com/training-courses/building-modern-web-apps-jump-start")

##Develop the user experience (15-20%)

###Plan for search engine optimization and accessibility

- Use analytical tools to parse HTML, 
	- [Google Webmaster Tools](https://www.google.com/webmasters "https://www.google.com/webmasters")
	- [Bing Webmaster Tools](http://www.bing.com/toolbox/webmaster "http://www.bing.com/toolbox/webmaster")
	- [IIS SEO Toolkit](http://www.iis.net/downloads/microsoft/search-engine-optimization-toolkit "http://www.iis.net/downloads/microsoft/search-engine-optimization-toolkit")
- view and evaluate conceptual structure by using plugs-in for browsers, 
- write semantic markup (HTML5 and ARIA) for accessibility (for example, screen readers)
- [SEO Ranking Guidelines](http://searchengineland.com/guide/seo "http://searchengineland.com/guide/seo")
	- Content is king - quality
	- Good domain name
	- Dynamic tags for dynamic content
		- Use dynamic title and meta tags (description) when content is dynamic/changing
	- Quality site structure
	- Link analysis and maintenance
		- Follow up and maintain good working links through SEO site analysis
	- Location and history
		- Make sure that redirects are handling properly (301s, not 304s)
		- Consistency is rewarded
	- Trustworthiness
		- Do not copy content to multiple pages\domains
		- Avoid keywords in titles
		- Make sure titles and meta tags are accurate

###Plan and implement globalization and localization

- Plan a [localization strategy](http://www.dotnetcurry.com/aspnet-mvc/1241/internationalization-aspnet-mvc-using-angularjs "http://www.dotnetcurry.com/aspnet-mvc/1241/internationalization-aspnet-mvc-using-angularjs")
- create and apply resources to UI, 
- including JavaScript resources; 
- set cultures; 
- create satellite resource assemblies

###Design and implement MVC controllers and actions

- Apply authorization attributes, [global filters](http://odetocode.com/blogs/scott/archive/2011/01/18/configurable-global-action-filters-for-asp-net-mvc.aspx "http://odetocode.com/blogs/scott/archive/2011/01/18/configurable-global-action-filters-for-asp-net-mvc.aspx"), and [authentication filters](https://visualstudiomagazine.com/articles/2013/08/28/asp_net-authentication-filters.aspx "https://visualstudiomagazine.com/articles/2013/08/28/asp_net-authentication-filters.aspx"); 
- specify an override filter; 
- implement [action behaviors](http://www.dotnetcurry.com/aspnet-mvc/1273/action-method-selector-parameters-aspnet-mvc "http://www.dotnetcurry.com/aspnet-mvc/1273/action-method-selector-parameters-aspnet-mvc"); 
- implement action results; 
- implement model binding

###Design and implement routes

- Define a route to handle a URL pattern, 
- apply route constraints, 
- ignore URL patterns, 
- add custom route parameters, 
- define areas
	- * apply routing relative to areas

###Control application behavior by using [MVC extensibility points](http://codeclimber.net.nz/archive/2009/04/08/13-asp.net-mvc-extensibility-points-you-have-to-know.aspx "http://codeclimber.net.nz/archive/2009/04/08/13-asp.net-mvc-extensibility-points-you-have-to-know.aspx")

- Implement MVC filters and controller factories; 
- control application behavior by using action results, viewengines, model binders, and route handlers

###[Reduce network bandwidth](http://failedturing.blogspot.com/2016/03/microsoft-70-486-reduce-network.html "http://failedturing.blogspot.com/2016/03/microsoft-70-486-reduce-network.html")

- Bundle and minify scripts (CSS and JavaScript), 
- compress and decompress data (using gzip/deflate; storage), 
- plan a content delivery network (CDN) strategy (for example, Azure CDN)

####Preparation resources

- [Search Engine Optimization Toolkit](http://www.iis.net/downloads/microsoft/search-engine-optimization-toolkit "http://www.iis.net/downloads/microsoft/search-engine-optimization-toolkit")
- [GlobalizationSection Class](http://msdn.microsoft.com/en-us/library/system.web.configuration.globalizationsection.aspx "http://msdn.microsoft.com/en-us/library/system.web.configuration.globalizationsection.aspx")
- [FormCollection Class](http://msdn.microsoft.com/en-us/library/system.web.mvc.formcollection(v=vs.118).aspx "http://msdn.microsoft.com/en-us/library/system.web.mvc.formcollection(v=vs.118).aspx")

##Troubleshoot and debug web applications (20-25%)

###Prevent and troubleshoot runtime issues

- Troubleshoot performance, security, and errors:
	- Performance profiling options (wizard):
		- CPU sampling (recommended) - minimal impact to application
		- Instrumentation - more invasive to working application
		- .NET memory allocation (sampling)
		- Resource contention data (concurrency) 
- implement tracing, logging (including using attributes for logging), and debugging (including [IntelliTrace](https://msdn.microsoft.com/en-us/library/dd264944(v=vs.120).aspx "https://msdn.microsoft.com/en-us/library/dd264944(v=vs.120).aspx")); 
- enforce conditions by using code contracts; 
- enable and configure health monitoring (including Performance Monitor)

###* Design an exception handling strategy

- Handle exceptions across [multiple layers](http://failedturing.blogspot.com/2016/03/microsoft-70-486-design-exception.html "http://failedturing.blogspot.com/2016/03/microsoft-70-486-design-exception.html")
	- Try/Catch
	- Business case (`var == null`) 
	- `ControllerClass.OnException()` override
	- `[HandleError]` attribute
	- `Application_Error` method in global.asax
- display custom error pages using global.asax or creating your own HTTPHandler or set web.config attributes, 
	- [HandleErrorAttribute](https://msdn.microsoft.com/en-us/library/system.web.mvc.handleerrorattribute.aspx "https://msdn.microsoft.com/en-us/library/system.web.mvc.handleerrorattribute.aspx")
- *[Handle first chance exceptions](https://msdn.microsoft.com/en-us/library/dd997368(v=vs.110).aspx "https://msdn.microsoft.com/en-us/library/dd997368(v=vs.110).aspx") 
		- registering AppDomain.CurrentDomain.FirstChanceException event in `Application_Start()` in global.asax, with output to email or log file

###Test a web application

- Create and run unit tests (for example, use the Assert class), 
- create mocks; 
- create and run web tests, including using Browser Link; 
- debug a web application in multiple browsers and mobile emulators

###* Debug an Azure application

- Collect diagnostic information by using Azure Diagnostics API and appropriately implement on demand versus scheduled; 
- choose log types (for example, event logs, performance counters, and crash dumps); 
- debug an Azure application by using IntelliTrace, Remote Desktop Protocol (RDP), and remote debugging; 
- interact directly with remote Azure websites using Server Explorer.

####Preparation resources

- [Using shims to isolate your application from other assemblies for unit testing](http://msdn.microsoft.com/en-us/library/hh549176(v=vs.120).aspx "http://msdn.microsoft.com/en-us/library/hh549176(v=vs.120).aspx")

##Design and implement security (20-25%)

###* Configure authentication

- Authenticate users; 
- enforce authentication settings; 
- Authentication options - choose between:
	- Windows - Best for intra-net sites and websites that have access to AD controllers, built-in to ASP.Net & IIS
	- Forms - Integrates with both identity- and claims-based authentication with built-in support for standard membership providers
	- custom authentication - Allows greater flexibility in user-store access and modification 
- manage user session by using cookies
	- Cookie storage - Allowing for 2K of data on client or can be stored at the server via Session management
	- Cookie persistence 
		- When enabled, this allows a client to close browser and return to site, maintaining the cookie
		- When disabled, the cookie expires once the session ends or the client closes the browser
	- Cookie reference - Allows the cookie to remain relatively small, as it only holds a reference to the data location on the server 
- configure membership providers
	- `SimpleMembership`
	- `SimpleRoles`
	- `SqlMembershipProvider`
- create custom membership providers
	- `MembershipProvider` vs `WebSecurity`
		- `MembershipProvider` is an abstract class which can be used to create a custom provider.
		- `WebSecurity` is a wrapper of `SimpleMembership` which allows easy access to many of the security methods contained therein.
			- `DeleteAccount()` is not implemented in this helper. 
		- `WebSecurity` is not interoperable with MembershipProvider, only with SimpleMembership.
- configure ASP.NET Identity
- WCF Authentication Security
	- Two basic mechanisms for WCF security
		- Transport: 
			- Message encrypted at the transport-level, leveraging whichever security mechanism the transport protocol uses (TCP: TLS; HTTPS: SSL)
			- Security is point-to-point and tends to have greater interoperability but any message forwarded beyond the service is not automatically encrypted.
			- Both caller credentials and message are encrypted between access points but are essentially separate(?)
			- Better performance and can benefit from hardware acceleration
		- Message:
			- Both the message and the caller's credentials are encrypted together using the WS-Security specification
			- Resulting payload is encrypted, even if forwarded, resulting in better overall security
			- Performance suffers:
				- this mechanism cannot benefit from hardware acceleration 
				- the message must be re-encrypted before it can be forwarded to other services
				- the WS-Security specification must be supported through the service pipeline
	- Security Modes
		- None. Messages are not secured.
		- Transport. Messages are secured using transport security. 
		- Message. Messages are secured using message security. 
		- TransportWithMessageCredential. Message protection and authorization occur at the transport level and credentials are passed with the message.
		- TransportCredentialOnly. Credentials are passed at the transport level but the message is not encrypted. This option is available only if you are using the BasicHttpBinding binding.
		- Both. Messages are secured using both transport level and message level security. This is supported only if you are using Microsoft Message Queue Server. 
	- Credential Types (Transport)
		- Windows. The client uses a Windows token representing the logged in user’s Windows identity. The service uses the credentials of the process identity or an SSL certificate. 
		- Basic. The client passes a user name and password to the service. Typically, the user will enter the user name and password in a login dialog box. The service uses a SSL certificate. This option is available only with HTTP protocols. 
		- Certificate. The client uses an X.509 certificate and the service uses either that certificate or an SSL certificate.
		- NTLM. The service validates the client using a challenge/response scheme against Windows accounts. The service uses a SSL certificate. This option is available only with the HTTPS protocol.
		- None. The service does not validate the client.
	- Credential Types (Message)
		- Windows. The client uses a Windows token representing the logged in user’s Windows identity. The service uses the credentials of the process identity or an SSL certificate. 
		- UserName. The client passes a user name and password to the service. Typically, the user will enter the user name and password in a login dialog box. The service can validate the user name and password using a Windows account or the ASP.NET membership provider. 
		- Certificate. The client uses an X.509 certificate and the service uses either that certificate or an SSL certificate.
		- IssueToken. The client and service use the Secure Token Service, which issues tokens the client and service trust. Windows CardSpace uses the Secure Token Service.
		- None. The service does not validate the client.
	- Config example


			<bindings>
			  <netTcpBinding>
			    <binding name="SecureService_Tcp"
			      …
			      <security mode="Transport">
			        <transport clientCredentialType="Windows"
			                   protectionLevel="EncryptAndSign" />
			        <message clientCredentialType="Windows" />
			      </security>
			    </binding>
			  </netTcpBinding>
			  <wsHttpBinding>
			    <binding name="SecureService_WsHttp"
			      …
			      <security mode="Message">
			        <transport clientCredentialType="Windows"
			                   proxyCredentialType="None"
			                   realm="" />
			        <message clientCredentialType="Windows"
			                 negotiateServiceCredential="true"
			                 algorithmSuite="Default"
			                 establishSecurityContext="true" />
			      </security>
			    </binding>
			  </wsHttpBinding>
			</bindings>

- WCF Authorization
	- Authorization Options
		- Role-based. Access to a service and to operations of the service is based on the user’s role. 
		- Identity based. Access is based on claims made within the user’s credentials. This is an extension to role-based authorization and provides a more fine grained approach. This approach will typically be used with issue token authentication.
		- Resource based. Resources, such as WCF services, are secured using Windows Access Control Lists (ACLs).
	- Role Determination Options
		- Windows groups. You can use the built-in Windows groups such as Administrators or Power Users or create your own Windows groups. 
		- Custom roles. You can create roles that are specific to your application, such as Manager, Employee, Administrator, etc.
		- ASP.NET role management. You can use the ASP.NET role provider and use roles you have defined for a Web site. 


###*Configure and apply authorization

- Create roles, authorize roles by [using configuration](http://www.dotnetcurry.com/aspnet-mvc/1268/access-action-method-multiple-user-roles-using-config "http://www.dotnetcurry.com/aspnet-mvc/1268/access-action-method-multiple-user-roles-using-config"), 
- authorize roles programmatically
	- `AuthorizeAttribute`
		- Decorate controllers and methods, specifying roles that have access
		- Roles or Users
- create custom role providers
	- Implement with `RoleProviderBase`
- implement [WCF service authorization](https://msdn.microsoft.com/en-us/library/ff405740.aspx "https://msdn.microsoft.com/en-us/library/ff405740.aspx")

###Design and implement claims-based authentication across federated identity stores

- Implement federated authentication by using Azure Access Control Service; 
- create a custom security token by using Windows Identity Foundation
	- Token definition (in xml)
		- contains the claims and signature definitions, as well as certificate information
	- Custom Token managed class, derived from `SecurityToken`
	- Custom TokenHandler managed class, derived from `SecurityTokenHandler`
		- Override the `CanValidateToken()` and `ValidateToken()` methods for the TokenHandler to be used and to properly parse the custom Token class, whose signature can then be validated
	- Custom TokenHandler needs to be added to app.config (Example):

			<?xml version="1.0" encoding="utf-8" ?>
			<configuration>
			  <configSections>
			    <!-- Registers the microsoft.IdentityModel configuration section -->
			    <section name="microsoft.identityModel" type="Microsoft.IdentityModel.Configuration.MicrosoftIdentityModelSection, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"/>
			  </configSections>
			  <microsoft.identityModel>
			    <service>
			      <securityTokenHandlers>
			        <remove type="Microsoft.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=31BF3856AD364E35"/>
			        <add type="SimpleCustomSecurityTokenHandler.CustomUserNamePasswordValidatorSecurityTokenHandler, SimpleCustomSecurityTokenHandler"/>
			      </securityTokenHandlers>
			    </service>
			  </microsoft.identityModel>
			</configuration>

(Note both the Remove and Add nodes specified, which prevents the default handler from executing before the custom handler can take action.)

- handle token formats (for example, oAuth, OpenID, Microsoft Account, Google, Twitter, and Facebook) for SAML and SWT tokens

###Manage data integrity

- Apply encryption to application data, 
- apply encryption to the configuration sections of an application 
	- set in the web.config or utilizes machine.config provider setting instance
	- `DPAPIProtectedConfigurationProvider`:
		- Uses the Windows Data Protection API for encryption/decryption
		- Appropriate for stand-alone web instances, utilizing the machine key
	- `RsaProtectedConfigurationProvider`:
		- Utilizes the RSA encryption algorithm
		- Supports exporting\importing of keys, allowing for multiple servers to share configuration files
	- `aspnet_regiis` with `-pe` switch
		- enables **provider encryption** on specific sections of web.config
		- to decrypt, replace the `-pe` switch with the `-pd` switch
		- example: `aspnet_regiis -pe "ConnectionStrings" -app "/TestApp" -prov "RsaProtectedConfigurationProvider"`
- sign application data to prevent tampering

###Implement a secure site with ASP.NET

- Secure communication by applying SSL certificates; 
- salt and hash passwords for storage; 
- use HTML encoding to prevent cross-site scripting attacks (ANTI-XSS Library); 
- * implement deferred validation and handle unvalidated requests, for example, form, querystring, and URL; 
- prevent SQL injection attacks by parameterizing queries; 
- prevent cross-site request forgeries (XSRF)

####Preparation resources

- [Introduction to ASP.NET Identity](http://www.asp.net/identity/overview/getting-started/introduction-to-aspnet-identity "http://www.asp.net/identity/overview/getting-started/introduction-to-aspnet-identity")
- [Chapter 5: Authentication, authorization, and identities in WCF](http://msdn.microsoft.com/en-us/library/ff647503.aspx "http://msdn.microsoft.com/en-us/library/ff647503.aspx")
- [Easy Web App Integration with Windows Azure Active Directory, ASP.NET & Visual Studio](http://blogs.technet.com/b/ad/archive/2013/06/26/improved-windows-azure-active-directory-integration-with-asp-net-amp-visual-studio.aspx "http://blogs.technet.com/b/ad/archive/2013/06/26/improved-windows-azure-active-directory-integration-with-asp-net-amp-visual-studio.aspx")