# Clean code
## Chapter 1 : Clean code
This book is for learn to code properly and become a good programmer
According to Bjarne Stroustrup, inventor of C++ he likes the code to be
elegant and efficient.

Meanwhile Grady Booch, author of Object
Oriented Analysis and Design with Applications says that a clean code is
simple and direct.

Grady Booch, author of Object Oriented Analysis and Design with Applications
says that the readability has to be one of the important things
for make clean code easier and easy for other people to enhance it.

Michael Feathers, author of Working Effectively with Legacy Code says that a subtitle 
for this book can be How to Care for Code.

Ron Jeffries, author of Extreme Programming Installed and Extreme Programming Adventures in C#
says things in priority order : 

Runs all tests; 

Contains no duplication;

Expresses all the design ideas that are in system; 

Minimizes the number of entities such as classes, methods, functions, and the like.
### The boy scout rule
The code has to be kept clean over the time, the boy scouts of America
have a simple rule that we can apply to our profession:
"Leave the campground cleaner than you found it."

So if we apply this into our code and check it a little cleaner
than we checked it out, the code simply could not root. The cleanup
doesn't have to be something big, change one variable name for one 
better, break up one function that's a little too large, eliminate
one small bit of duplication, clean up one composite if statement.
### Conclusion
Just like a book on art, this book will be full of details. There will be lots of code.
You’ll see good code and you’ll see bad code. You’ll see bad code transformed into good
code. You’ll see lists of heuristics, disciplines, and techniques. You’ll see example after
example. After that, it’s up to you
## Chapter 2 : Meaningful Names 
### Introduction
Names are everywhere in software. We name our variables, our functions, our arguments,
classes, and packages. We name our source files and the directories that contain them. We
name our jar files and war files and ear files. We name and name and name.

### Use Intention-Revealing Names
Choosing good names takes time but saves more than it takes.
So take care with your names and change them when you find better ones. Everyone who
reads your code (including you) will be happier if you do.

For example :

int d; // elapsed time in days

The name d reveals nothing. It does not evoke a sense of elapsed time, nor of days. We
should choose a name that specifies what is being measured and the unit of that measurement:

int elapsedTimeInDays;

int daysSinceCreation;

int daysSinceModification;

int fileAgeInDays;

Choosing names that reveal intent can make it much easier to understand and change
code.

### Avoid Disinformation
Programmers must avoid leaving false clues that obscure the meaning of code. We should
avoid words whose entrenched meanings vary from our intended meaning. For example,
hp, aix, and sco would be poor variable names because they are the names of Unix platforms or variants.
Even if you are coding a hypotenuse and hp looks like a good abbreviation, it could be disinformative.
### Use Pronounceable Names
Humans are good at words. A significant part of our brains is dedicated to the concept of
words. And words are, by definition, pronounceable. It would be a shame not to take
advantage of that huge portion of our brains that has evolved to deal with spoken language.
So make your names pronounceable.
### Use Searchable Names
Single-letter names and numeric constants have a particular problem in that they are not
easy to locate across a body of text.

One might easily grep for MAX_CLASSES_PER_STUDENT, but the number 7 could be more
troublesome. Searches may turn up the digit as part of file names, other constant definitions, and in various expressions where the value is used with different intent. It is even
worse when a constant is a long number and someone might have transposed digits,
thereby creating a bug while simultaneously evading the programmer’s search.

Likewise, the name e is a poor choice for any variable for which a programmer might
need to search.
## Chapter 3 : Functions
### Small!
The first rule of functions is that they should be small. The second rule of functions is that
they should be smaller than that. This assertion can't be justified and provide that very small
functions are better but according to her experience he can tell that in four decades writing functions
of all sizes, 3000 lines, 100 to 300 lines range and 20 to 30 lines long, functions should be very small.
### Blocks and Indenting
This implies that the blocks within if statements, else statements, while statements, and 
so on should be one line long. Probably that line should be a function call. Not only does
this keep the enclosing function small, but it also adds documentary value because the
function called within the block can have a nicely descriptive name.
### Do one thing
The following advice has appeared in one form or another for 30 years or more : 

FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL.
THEY SHOULD DO IT ONLY.

### One Level of Abstraction per Function
We need to make sure that the statements within our function are all at the same level of abstraction.
There are concepts in there that are at a very high level of
abstraction, such as getHtml(); others that are at an intermediate level of abstraction, such
as: String pagePathName = PathParser.render(pagePath); and still others that are remarkably low level, such as: .append("\n").
Mixing levels of abstraction within a function is always confusing. Readers may not
be able to tell whether a particular expression is an essential concept or a detail.
### Reading Code from Top to Bottom: The Stepdown Rule
We want the code to read like a top-down narrative. We want every function to be followed
by those at the next level of abstraction so that we can read the program, descending one level
of abstraction at a time as we read down the list of functions.
To say this differently, we want to be able to read the program as though it were a set
of TO paragraphs, each of which is describing the current level of abstraction and referencing subsequent TO paragraphs at the next level down.
### Function arguments
Arguments are even harder from a testing point of view. Imagine the difficulty of
writing all the test cases to ensure that all the various combinations of arguments work
properly. If there are no arguments, this is trivial. If there’s one argument, it’s not too hard.
With two arguments the problem gets a bit more challenging. With more than two arguments, testing
every combination of appropriate values can be daunting.
### Structured Programming
Some programmers follow Edsger Dijkstra’s rules of structured programming. Dijkstra
said that every function, and every block within a function, should have one entry and one
exit. Following these rules means that there should only be one return statement in a function,
no break or continue statements in a loop, and never, ever, any goto statements.

So if you keep your functions small, then the occasional multiple return, break, or
continue statement does no harm and can sometimes even be more expressive than the single-entry, single-exit rule. On the other hand, goto only makes sense in large functions, so
it should be avoided.
### Conclusion
This chapter has been about the mechanics of writing functions well. If you follow
the rules herein, your functions will be short, well named, and nicely organized. But
never forget that your real goal is to tell the story of the system, and that the functions
you write need to fit cleanly together into a clear and precise language to help you with
that telling.
## Chapter 4 : Comments
### Comments Do Not Make Up for Bad Code
Clear and expressive code with few comments is far superior to cluttered and complex
code with lots of comments. Rather than spend your time writing the comments that
explain the mess you’ve made, spend it cleaning that mess.
### Explain Yourself in Code
Which would you rather see? This:

// Check to see if the employee is eligible for full benefits
if ((employee.flags & HOURLY_FLAG) &&
(employee.age > 65))

Or this?

if (employee.isEligibleForFullBenefits())

It takes only a few seconds of thought to explain most of your intent in code.
### Good Comments
Some comments are necessary or beneficial. We’ll look at a few that I consider worthy of
the bits they consume. Keep in mind, however, that the only truly good comment is the
comment you found a way not to write.
### Legal Comments
Sometimes our corporate coding standards force us to write certain comments for legal
reasons. For example, copyright and authorship statements are necessary and reasonable
things to put into a comment at the start of each source file.

Here, for example, is the standard comment header that we put at the beginning of
every source file in FitNesse. I am happy to say that our IDE hides this comment from acting as clutter by automatically collapsing it.

// Copyright (C) 2003,2004,2005 by Object Mentor, Inc. All rights reserved.
// Released under the terms of the GNU General Public License version 2 or later.

Comments like this should not be contracts or legal tomes.
### Informative comments
It is sometimes useful to provide basic information with a comment. 
For example, consider this comment that explains the return value of an abstract method:

// Returns an instance of the Responder being tested.
protected abstract Responder responderInstance();

A comment like this can sometimes be useful, but it is better to use the name of the function to convey the 
information where possible.
### Bad Comments
Most comments fall into this category. Usually they are crutches or excuses for poor code
or justifications for insufficient decisions, amounting to little more than the programmer
talking to himself.
### Mumbling
Plopping in a comment just because you feel you should or because the process requires it,
is a hack. If you decide to write a comment, then spend the time necessary to make sure it
is the best comment you can write. 

public void loadProperties()
{
try
{
String propertiesPath = propertiesLocation + "/" + PROPERTIES_FILE;
FileInputStream propertiesStream = new FileInputStream(propertiesPath);
loadedProperties.load(propertiesStream);
}
catch(IOException e)
{
// No properties files means all defaults are loaded
}
}
### Mandated Comments
It is just plain silly to have a rule that says that every function must have a javadoc, or
every variable must have a comment.

For example, required javadocs for every function lead to abominations such as Listing 4-3. This clutter adds nothing and serves only to obfuscate the code and create the
potential for lies and misdirection.

Listing 4-3
/**
*
* @param title The title of the CD
* @param author The author of the CD
* @param tracks The number of tracks on the CD
* @param durationInMinutes The duration of the CD in minutes
  */
  public void addCD(String title, String author,
  int tracks, int durationInMinutes) {
  CD cd = new CD();
  cd.title = title;
  cd.author = author;
  cd.tracks = tracks;
  cd.duration = duration;
  cdList.add(cd);
  }
### Journal Comments
Sometimes people add a comment to the start of a module every time they edit it. These
comments accumulate as a kind of journal, or log, of every change that has ever been
made.

* Changes (from 11-Oct-2001)
* --------------------------
* 11-Oct-2001 : Re-organised the class and moved it to new package
* com.jrefinery.date (DG);
* 05-Nov-2001 : Added a getDescription() method, and eliminated NotableDate
* class (DG);
* 12-Nov-2001 : IBD requires setDescription() method, now that NotableDate
* class is gone (DG); Changed getPreviousDayOfWeek(),
* getFollowingDayOfWeek() and getNearestDayOfWeek() to correct
* bugs (DG);
* 05-Dec-2001 : Fixed bug in SpreadsheetDate class (DG);
* 29-May-2002 : Moved the month constants into a separate interface
* (MonthConstants) (DG);
* 27-Aug-2002 : Fixed bug in addMonths() method, thanks to N???levka Petr (DG);
* 03-Oct-2002 : Fixed errors reported by Checkstyle (DG);
* 13-Mar-2003 : Implemented Serializable (DG);
* 29-May-2003 : Fixed bug in addMonths method (DG);
* 04-Sep-2003 : Implemented Comparable. Updated the isInRange javadocs (DG);
* 05-Jan-2005 : Fixed bug in addYears() method (1096282) (DG);
### Noise Comments
Sometimes you see comments that are nothing but noise. They restate the obvious and
provide no new information.

/**
* Default constructor.
  */
  protected AnnualDateRule() {
  }
  No, really? Or how about this:
  /** The day of the month. */
  private int dayOfMonth;
  And then there’s this paragon of redundancy:
  /**
* Returns the day of the month.
*
* @return the day of the month.
  */
  public int getDayOfMonth() {
  return dayOfMonth;
  }
### Don't use a Comment When You Can Use a Function or a Variable
Consider the following stretch of code:

// does the module from the global list <mod> depend on the
// subsystem we are part of?
if (smodule.getDependSubsystems().contains(subSysMod.getSubSystem()))

This could be rephrased without the comment as

ArrayList moduleDependees = smodule.getDependSubsystems();
String ourSubSystem = subSysMod.getSubSystem();
if (moduleDependees.contains(ourSubSystem))

The author of the original code may have written the comment first (unlikely) and then
written the code to fulfill the comment.
## Chapter 5 : Formatting
### The Purpose of Formatting
Code formatting is important. It is too important to ignore and
it is too important to treat religiously. Code formatting is about communication, and
communication is the professional developer’s first order of business. 

So what are the formatting issues that help us to communicate best?
### Vertical Formating
How big should a source file be? In Java, file size is closely
related to class size. We’ll talk about class size when we talk about classes. For the
moment let’s just consider file size.
### The Newspaper Metaphor
Think of a well-written newspaper article. You read it vertically. At the top you expect a
headline that will tell you what the story is about and allows you to decide whether it is
something you want to read.

We would like a source file to be like a newspaper article. The name should be simple
but explanatory. The name, by itself, should be sufficient to tell us whether we are in the
right module or not. 
### Vertical Openness Between Concepts
Nearly all code is read left to right and top to bottom. Each line represents an expression or
a clause, and each group of lines represents a complete thought. Those thoughts should be
separated from each other with blank lines.
### Vertical Density
If openness separates concepts, then vertical density implies close association. So lines
of code that are tightly related should appear vertically dense. Notice how the useless
comments in Listing 5-3 break the close association of the two instance variables. 

Listing 5-3

public class ReporterConfig {
/**
* The class name of the reporter listener
  */
  private String m_className;
  /**
* The properties of the reporter listener
  */
  private List<Property> m_properties = new ArrayList<Property>();
  public void addProperty(Property property) {
  m_properties.add(property);
  }
### Vertical Distance
Variable Declarations. Variables should be declared as close to their usage as possible. Because our functions are very short, local variables should appear a the top of each
function, as in this longish function from Junit4.3.1. 

private static void readPreferences() {
InputStream is= null;
try {
is= new FileInputStream(getPreferencesFile());
setPreferences(new Properties(getPreferences()));
getPreferences().load(is);
} catch (IOException e) {
try {
if (is != null)
is.close();
} catch (IOException e1) {
}
}
}

Instance variables, on the other hand, should be declared at the top of the class. This
should not increase the vertical distance of these variables, because in a well-designed
class, they are used by many, if not all, of the methods of the class.

Dependent Functions. If one function calls another, they should be vertically close,
and the caller should be above the callee, if at all possible. This gives the program a natural
flow. 

Conceptual Affinity. Certain bits of code want
to be near other bits. They have a certain
conceptual affinity. The stronger that affinity, the
less vertical distance there should be between
them.
### Vertical Ordering
In general we want function call dependencies to point in the downward direction. That is,
a function that is called should be below a function that does the calling. This creates a
nice flow down the source code module from high level to low level. 
### Horizontal Formating
### Horizontal Openness and Density
We use horizontal white space to associate things that are strongly related and disassociate
things that are more weakly related. Consider the following function:

private void measureLine(String line) {
lineCount++;
int lineSize = line.length();
totalChars += lineSize;
lineWidthHistogram.addLine(lineSize, lineCount);
recordWidestLine(lineSize);
}
### Horizontal Alignment
When I started coding in C, C++, and eventually Java, I continued to try
to line up all the variable names in a set of declarations, or all the rvalues in a set of assignment statements. 
My code might have looked like this:

public class FitNesseExpediter implements ResponseSender

{

private Socket socket;

private InputStream input;

private OutputStream output;

private Request request;

private Response response;

private FitNesseContext context;

protected long requestParsingTimeLimit;

private long requestProgress;

private long requestParsingDeadline;

private boolean hasError;

public FitNesseExpediter(Socket s,

                    FitNesseContext context) throws Exception

{

this.context = context;

socket = s;

input = s.getInputStream();

output = s.getOutputStream();

requestParsingTimeLimit = 10000;

}

I have found, however, that this kind of alignment is not useful. The alignment seems to
emphasize the wrong things and leads my eye away from the true intent.
### Indentation
A source file is a hierarchy rather like an outline. There is information that pertains to the
file as a whole, to the individual classes within the file, to the methods within the classes,
to the blocks within the methods, and recursively to the blocks within the blocks. 

To make this hierarchy of scopes visible, we indent the lines of source code in proportion to their position in the hiearchy. Statements at the level of the file, such as most
class declarations, are not indented at all. Methods within a class are indented one level
to the right of the class. Implementations of those methods are implemented one level to
the right of the method declaration. Block implementations are implemented one level
to the right of their containing block, and so on.
### Dummy Scopes
Sometimes the body of a while or for statement is a dummy, as shown below. I don’t like
these kinds of structures and try to avoid them. When I can’t avoid them, I make sure that
the dummy body is properly indented and surrounded by braces.
### Team Rules
Every programmer has his own favorite formatting rules, but if he works in a team, then the team rules. 

A team of developers should agree upon a single formatting style, and then every member of that team
should use that style. We want the software to have a consistent style.

Remember, a good software system is composed of a set of documents that read
nicely. 
## Chapter 7 : Error Handling
### Use Exceptions Rather Than Return Codes
Back in the distant past there were many languages that didn’t have exceptions. In those
languages the techniques for handling and reporting errors were limited. You either set an
error flag or returned an error code that the caller could check.
### Write Your Try-Catch-Finally Statement First
Let’s look at an example. We need to write some code that accesses a file and reads
some serialized objects.

We start with a unit test that shows that we’ll get an exception when the file doesn’t exist:

@Test(expected = StorageException.class)

public void retrieveSectionShouldThrowOnInvalidFileName() {
sectionStore.retrieveSection("invalid - file");

}

The test drives us to create this stub:

public List<RecordedGrip> retrieveSection(String sectionName) {

// dummy return until we have a real implementation
return new ArrayList<RecordedGrip>();

}

Our test fails because it doesn’t throw an exception.
### Use Unchecked Exceptions
For years Java programmers have debated over the benefits and liabilities of checked exceptions. When checked exceptions were introduced in the first version
of Java, they seemed like a great idea. The signature of every method would list all of the
exceptions that it could pass to its caller. Moreover, these exceptions were part of the type
of the method. Your code literally wouldn’t compile if the signature didn’t match what your
code could do. 

At the time, we thought that checked exceptions were a great idea; and yes, they can
yield some benefit. However, it is clear now that they aren’t necessary for the production of
robust software. C# doesn’t have checked exceptions, and despite valiant attempts, C++
doesn’t either. Neither do Python or Ruby. Yet it is possible to write robust software in all
of these languages.

What price? The price of checked exceptions is an Open/Closed Principle violation.
If you throw a checked exception from a method in your code and the catch is three levels
above, you must declare that exception in the signature of each method between you and
the catch. This means that a change at a low level of the software can force signature
changes on many higher levels. The changed modules must be rebuilt and redeployed,
even though nothing they care about changed. 

Checked exceptions can sometimes be useful if you are writing a critical library: You
must catch them. But in general application development the dependency costs outweigh
the benefits.
### Provide Context with Exceptions
Each exception that you throw should provide enough context to determine the source and
location of an error.

Create informative error messages and pass them along with your exceptions. Mention the operation that failed and
the type of failure. If you are logging in your application,
pass along enough information to be able to log the error in your catch.
### Define Exception Classes in Terms of a Caller's Needs
There are many ways to classify errors. We can classify them by their source: Did they
come from one component or another? Or their type: Are they device failures, network
failures, or programming errors? However, when we define exception classes in an application,
our most important concern should be how they are caught.

Let’s look at an example of poor exception classification :

ACMEPort port = new ACMEPort(12);

try {

port.open();

} catch (DeviceResponseException e) {

reportPortError(e);

logger.log("Device response exception", e);

} catch (ATM1212UnlockedException e) {

reportPortError(e);

logger.log("Unlock exception", e);

} catch (GMXError e) {

reportPortError(e);

logger.log("Device response exception");

} finally {

  …

}

That statement contains a lot of duplication, and we shouldn’t be surprised. In most
exception handling situations, the work that we do is relatively standard regardless of the
actual cause. We have to record an error and make sure that we can proceed.

In this case, because we know that the work that we are doing is roughly the same
regardless of the exception, we can simplify our code considerably by wrapping the API
that we are calling and making sure that it returns a common exception type.
### Define the Normal Flow
If you follow the advice in the preceding sections, you’ll end up with a good amount
of separation between your business logic and your error handling.

Let’s take a look at an example. Here is some awkward code that sums expenses in a
billing application:

try {

MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());

m_total += expenses.getTotal();

} catch(MealExpensesNotFound e) {

m_total += getMealPerDiem();

}

In this business, if meals are expensed, they become part of the total. If they aren’t, the
employee gets a meal per diem amount for that day. The exception clutters the logic.
Wouldn’t it be better if we didn’t have to deal with the special case? If we didn’t, our code
would look much simpler. It would look like this:

MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());

m_total += expenses.getTotal();
### Conclusion
Clean code is readable, but it must also be robust. These are not conflicting goals. We can
write robust clean code if we see error handling as a separate concern, something that is
viewable independently of our main logic. To the degree that we are able to do that, we can
reason about it independently, and we can make great strides in the maintainability of our
code.