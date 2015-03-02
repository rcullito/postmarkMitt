# Postmark Mitt

This set of case classes and their accompanying readers is meant to be used to help parse inbound mail with [Postmark](http://developer.postmarkapp.com/developer-process-parse.html).  

An example use case for it might be as follows:

    import models.Postmark
    
    val source = scala.io.Source.fromFile("exampleWebHookAllFields.json")
    val postMarkResult = Postmark.parseJson(source.mkString)
    
    postMarkResult match {
      case s: JsSuccess[postMarkMitt] => val result = s.get
          // additional fields accessible as attributes off of result
          println(result.attachments.length.toString())
    }
