Telemetry
=========

1. Clone this repository.
2. Create a new branch.
3. Write a small express 4.x application that handles a telemetry stream. Feel free to use other npm modules too.

	The goal of the application is to perform pattern recognition on a stream of messages where each message contains a character. The server should maintain a suitable data structure whose input is json received on route `/rules/update` and should attempt to recognize these patterns in the stream of incoming messages on route `message/create`. When the server recognizes a pattern it should append the rule's output to a file.

	## Routes

	The application should have two routes. 

	```
	/rules/update
	/message/create
	```

	The message route will accept json in this form. Assume all messages only contain one character.

	```
	{
		string: "A"
	}
	```

	The rules route will accept json in this form.

	```
	{
		"ABABBA": "foo",
		"ABBBBA": "bar",
		"ABB": "baz"
		// etc
	}
	```

	At any time it should be possible to overwrite the rules with a new set and any current pattern state should be discarded.
	
	When the server recognizes a pattern matching one of the rules object's keys it should write the corresponding value to the output file.

4. When the server works write a couple tests that verify the server works as expected. A single "works with the right input" test and a single "doesnt work with the wrong input" test is plenty, no need to go crazy here. If you're comfortable with Mocha and Chai those are preferred, but other test frameworks and assertion modules work fine too. 

5. Package up your submission as a zip or tar.gz file and email it to alec at azuqua dot com.
