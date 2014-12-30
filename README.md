# Struts2 PDF stream Plug-in

The PDF stream plugin allows to transform a view into a PDF stream and return it as a result from Action. 

Supported views:

- JSP-s
- FreeMarker templates
- Apache Tiles 2.x definitions
- Apache Tiles 3.x definitions


## Features Overview

- Direct transformation of JSP-s, FreeMarker templates and Apache Tiles definitions to PDF via Struts2 result
- PDF content styling using CSS
- Support of wide range of characters in PDF thanks to the [DejaVu fonts](http://dejavu-fonts.org/)
- Can process even malformed HTML thanks to the [jsoup](http://jsoup.org/)


## Installation

Copy struts2-pdfstream-plugin-x.x.x.jar into your classpath (WEB-INF/lib). No other files need to be copied or created.

If you are using Maven, add this to your project POM:

    <dependencies>
        ...
        <dependency>
            <groupId>com.amashchenko.struts2.pdfstream</groupId>
            <artifactId>struts2-pdfstream-plugin</artifactId>
            <version>1.2.2</version>
        </dependency>
        ...
    </dependencies>

If you intend to transform Apache Tiles definition additional jar must be included.

For the Apache Tiles 2.x support the `struts2-pdfstream-tiles`.

        <dependency>
            <groupId>com.amashchenko.struts2.pdfstream</groupId>
            <artifactId>struts2-pdfstream-tiles</artifactId>
            <version>1.2.2</version>
        </dependency>
        
For the Apache Tiles 3.x support the `struts2-pdfstream-tiles3`.

        <dependency>
            <groupId>com.amashchenko.struts2.pdfstream</groupId>
            <artifactId>struts2-pdfstream-tiles3</artifactId>
            <version>1.2.2</version>
        </dependency>


## Usage

1. Install this plugin by adding dependency to your POM or by copying jar into /WEB-INF/lib directory.
2. Make your action package extend `pdfstream-default` package or add `pdfstream` result type.
3. Use `pdfstream` result type.


## Examples

### JSP to PDF stream

        <action name="jspToPdf" class="com.amashchenko.struts2.pdfstream.showcase.PdfStreamAction">
            <result type="pdfstream">
                <param name="location">/WEB-INF/pages/table.jsp</param>
                <param name="cssPaths">css/bootstrap.min.css, css/style.css</param>
                <param name="contentDisposition">attachment;filename=jsppdf.pdf</param>
            </result>
        </action>

### Tiles definition to PDF stream

        <action name="tilesToPdf" class="com.amashchenko.struts2.pdfstream.showcase.PdfStreamAction">
            <result type="pdfstream">
                <param name="location">table</param>
                <param name="renderer">tiles</param>
                <param name="contentDisposition">attachment;filename=tilespdf.pdf</param>
            </result>
        </action>

### FreeMarker template to PDF stream

        <action name="freemarkerToPdf" class="com.amashchenko.struts2.pdfstream.showcase.PdfStreamAction">
            <result type="pdfstream">
                <param name="location">/WEB-INF/ftl/table.ftl</param>
                <param name="renderer">freemarker</param>
                <param name="cssPaths">css/bootstrap.min.css, css/style.css</param>
                <param name="contentDisposition">attachment;filename=ftlpdf.pdf</param>
            </result>
        </action>
