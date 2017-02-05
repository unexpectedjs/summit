# Unexpected summit

Planing repository for the summit.

Feel free to change the files in the repository directly on master.

There is some information on the earlier planing issue that can be found [here](https://github.com/unexpectedjs/unexpected/issues/337). Let's migretate the important information to this repo.

# Time and place

February 18th at Zendesk ([map](https://www.google.dk/maps/place/Zendesk+ApS/@55.6769832,12.5741805,17z/data=!3m1!4b1!4m5!3m4!1s0x4652531141140fcd:0xb16e28f41a8f0d08!8m2!3d55.6769802!4d12.5763692?hl=en))

# Agenda

* State of Unexpected (Sune)
* ...

TODO

# Discussion

- Output
  Unexpected provides extremely high quality output that usefully describes failures and critically is helpful in diagnosing/correcting problems. That said, it is probably fair to say we’ve erred on the side of outputting more (absolutely the correct default) but that this has been strained in a few cases dealing with huge amounts of data or large objects etc.
  
  _Discuss changes and/or specific rules around the output we generate._
- Context
  Our flexible plugin APIs have allowed extensins of growing complexity, many of which modify their environment (unexpected-fs, unexpected-mitm, unexpected-mxhr). While these assertions work well individually, issues arise for composition and inspecting the changed environment (unexpected-couchdb) requires complex one off solutions. In addition, a number plugins that provide assertions of ‘local system state’ would benefit from such support (e.g. unexpected-event).
  
  _Discuss context as a generic API to address these use-cases._
- Plugin versioning
  The Unexpected plugin system was designed primarily for node projects. While we have been able to enforce various package.json conventions that avoid versioning issues, static builds of Unexpected plugins for use within the browser can cause problems when they share underlying dependencies.
  
  _Discuss strategies for isolating plugin internals from end-user test suites._
- Challenges running tests
  Unexpected integrates with existing test running infrastructure through the assertion raising mechanism. However Unexpected would otherwise be able to give much more useful output for smaller chunks of failing tests, this is becoming a limitation. In addition, a large amount of complexity exists in the implementation supporting synchronous throws and also creates the plugin author footgun requiring an addition level of `expect.promise(function () { … })` wrapping.
  
  _Discuss alternative test running strategies._
