# StrutsExample

Block listed parameters:
CVE-2006-1546 org.apache.struts.taglib.html.CANCEL=true  and  org.apache.struts.taglib.html.CANCEL.x -> If any of these parameters are present  in request then we should need to log it and throw an exception.

CVE-2014-0114:   If request parameter contains a reference to class as part of its name then log it and throw an exception. Below are few examples of those,
class.classLoader.resources.context.parent.pipeline.first.directory=webapps/ROOT
class.classLoader.resources.context.parent.pipeline.first.prefix=shell
class.classLoader.resources.context.parent.pipeline.first.suffix=.jsp
class.classLoader.resources.context.parent.pipeline.first.fileDateFormat=12

During logging the parameter we need to encode it to avoid any further XSS issues for that we need to update the attached changes to take care of encoding. Can you please let me know if Alliance has this StringEscapeUtils.java class in use? We can use this to encode parameter for html encoding.
