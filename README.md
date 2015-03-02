## Postmark Mitt

This set of case classes and their accompanying readers is meant to be used to help parse inbound mail with [Postmark](http://developer.postmarkapp.com/developer-process-parse.html).

It is assumed to be used with the [Play](https://www.playframework.com/) Framework for both parsing and validating the incoming JSON request, and as such, relies on two of Play's internal libraries.

An example use case for it might be as follows:

    import models.Postmark
    
    val source = scala.io.Source.fromFile("exampleWebHookAllFields.json")
    val postMarkResult = Postmark.parseJson(source.mkString)
    
    postMarkResult match {
      case s: JsSuccess[postMarkMitt] => val result = s.get
          // additional fields accessible as attributes off of result
          println(result.attachments.length.toString())
    }
