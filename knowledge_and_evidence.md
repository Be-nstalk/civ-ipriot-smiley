<style>

body {
    counter-reset: h2counter;
}

/* H1 - No numbering */
h1 {
    /* No counter reset or increment */
}

/* H2 - Level 1 numbering */
h2 {
    counter-reset: h3counter;
}

h2::before {
    counter-increment: h2counter;
    content: counter(h2counter) ". ";
}

/* H3 - Level 2 numbering */
h3 {
    counter-reset: h4counter;
}

h3::before {
    counter-increment: h3counter;
    content: counter(h2counter) "." counter(h3counter) " ";
}

/* H4 - Level 3 numbering (optional) */
h4 {
    counter-reset: h5counter;
}

h4::before {
    counter-increment: h4counter;
    content: counter(h2counter) "." counter(h3counter) "." counter(h4counter) " ";
}

</style>

# Evidence and Knowledge

This document includes instructions and knowledge questions that must be completed to receive a *Competent* grade on this portfolio task.

## Required evidence

### Answer all questions in this document

- Each answer should be complete, well-articulated, and within the specified word count limits (if added) for each question.
- Please make sure **all** external sources are properly cited.
- You must **use your own words**. Please include your full chat transcripts if you use generative AI in any way.
- Generative AI hallucinates, is not an authoritative source

### Make all the required modifications to the code

- Please follow the instructions in this document to make the changes needed to the code.

- When requested to upload evidence, upload all screenshots to `screenshots/` and embed them in this document. For example:

```markdown
![Example Running Code](screenshots/screenshot1.png)
```

- You must upload the code into your GitHub repository.
- While you can use a branch, your code should be in main when you submit.
- Upload a zip of this repository to Blackboard when you are ready to submit.
- You will be notified of your result via Blackboard
- However, if using GitHub classrooms, you may also receive additional feedback on GitHub directly

### Optional: Use of Raspberry Pi and SenseHat

Raspberry Pi or SenseHat is **optional** for this activity. You can use the included `sense_hat.py` file to simulate the SenseHat on your computer.

If you use a Pi, please **delete** the `sense_hat.py` file.

### Accessible version of the code

This project relies on visual patterns that appear on an LED matrix. If you have any accessibility requirements, you can use the `udl/accessible` branch to complete the project. This branch provides an accessible code version that uses text-based patterns instead of visual ones.

Please discuss this with your lecturer before using that branch.

## Specific Tasks & Questions

Address the following tasks and questions based on the code provided in this repository.

### Set up the project locally

1. Fork this repository (if not using GitHub Classrooms)
2. Clone your repository locally
3. Run the project locally by executing the `main.py` file
4. Evidence this by providing screenshots of the project directory structure and the output of the `main.py` file

![Local Execution (INSERT YOUR SCREENSHOT)](image.png)
![Directory](Screenshot_2.png)

If you are running on a Raspberry Pi, you can use the following command to run the project and then screenshot the result:

```bash
ls
python3 main.py
```

### Fundamental code comprehension

 Answer each of the following questions **as they relate to that code** supplied by in this repository (ignore `sense_hat.py`):

1. Examine the code for the `smiley.py` file and provide  an example of a variable of each of the following types and their corresponding values (`_` should be replaced with the appropriate values):

   | Type                    | name     | value           |
   | ----------------------- | -------- | --------------- |
   | built-in primitive type | *dimmed* | True            |
   | built-in composite type | *WHITE*  | (255, 255, 255) |
   | user-defined type       | Smiley   | `self.pixels`   |

2. Fill in (`_`) the following table based on the code in `smiley.py`:

   | Object                  | Type                       |
   | ----------------------- | -------------------------- |
   | self.pixels             | built-in composite (list)  |
   | A member of self.pixels | built-in composite (tuple) |
   | self                    | user-defined               |

3. Examine the code for `smiley.py`, `sad.py`, and `happy.py`. Give an example of each of the following control structures using an example from **each** of these files. Include the first line and the line range:

   | Control Flow | File        | First line           | Lines |
   | ------------ | ----------- | -------------------- | ----- |
   | sequence     | `smiley.py` | `WHITE = (255, 255, 255)` | 5-9 |
   | selection    | `sad.py`    | `if wide_open:`      | 26-29 |
   | iteration    | `happy.py`  | `for pixel in eyes:` | 30-31 |

4. Though everything in Python is an object, it is sometimes said to have four "primitive" types. Examining the three files `smiley.py`, `sad.py`, and `happy.py`, identify which of the following types are used in any of these files, and give an example of each (use an example from the code, if applicable, otherwise provide an example of your own):

   | Type  | Used? | Example                          |
   | ----- | ----- | -------------------------------- |
   | int   | Yes   | `Happy.draw_mouth()`: `mouth[0]` |
   | float | Yes   | `Happy.blink()`: `delay`         |
   | str   | Yes   | `Smiley.show()`: """Show the smiley on the screen."""? |
   | bool  | Yes   | `Sad.draw_eyes()`: `wide_open`   |

5. Examining `smiley.py`, provide an example of a class variable and an instance variable (attribute). Explain **why** one is defined as a class variable and the other as an instance variable.

   > Class variable `WHITE` defines a shared, static value accessible by all class instances.
   >
   > Instance variable `self.pixels` defines attributes unique to each class instance (requires initialisation).

6. Examine `happy.py`, and identify the constructor (initializer) for the `Happy` class:
   1. What is the purpose of a constructor (in general) and this one (in particular)?

      > The `__init__()` constructor is used to initialise a class instance, in this case, of the class `Happy`, by drawing the relevant features of the `Smiley`.

   2. What statement(s) does it execute (consider the `super` call), and what is the result?

      > `__init__` calls `super().__init__()` (the initialiser for the superclass `Smiley`), `draw_mouth()` and `draw_eyes()`, thus displaying a blank face onto which a recognisably happy visage is drawn.

### Code style

1. What code style is used in the code? Is it likely to be the same as the code style used in the SenseHat? Give to reasons as to why/why not:

   > It seems to follow PEP8 styling. This is likely also common to the SenseHat code, as it's a popular and well-established library, and PEP8 is standard for Python formatting.

2. List three aspects of this convention you see applied in the code.

   > - Snake-case formatting: `draw_mouth`, `wide_open`
   > - All-caps constants: `BLANK`
   > - Concise, descriptive docstrings: `"""Renders a mouth by blanking the pixels that form that object."""`

3. Give two examples of organizational documentation in the code.

   > Docstrings, inline comments.

### Identifying and understanding classes

> Note: Ignore the `sense_hat.py` file when answering the questions below

1. List all the classes you identified in the project. Indicate which classes are base classes and which are subclasses. For subclasses, identify all direct base classes.
  
   Use the following table for your answers:

   | Class Name | Super or Sub? | Direct parent(s) |
   | ---------- | ------------- | ---------------- |
   | Smiley     | Super         | None             |
   | Happy      | Sub           | Smiley           |
   | Sad        | Sub           | Smiley           |

2. Explain the concept of abstraction, giving an example from the project (note "implementing an ABC" is **not** in itself an example of abstraction). (Max 150 words)

   > Abstraction refers to the design of software components in such a way that they can be used without being understood, for example `draw_mouth()` in `happy.py` allows a visual representation of a mouth to be drawn without referring to specific pixels.

3. What is the name of the process of deriving from base classes? What is its purpose in this project? (Max 150 words)

   > Inheritance. In this project, it allows the `Happy` class to exist, along with all the properties of the `Smiley` and `Blinkable` classes from which it inherits, without defining those properties again.

### Compare and contrast classes

Compare and contrast the classes Happy and Sad.

1. What is the key difference between the two classes?
   > Only `Happy` inherits from `Blinkable` and implements `blink()`. The only difference between the two `draw_mouth` methods is the array used to define the mouth shape. `Sad` is also missing a docstring.
   >
2. What are the key similarities?
   > They both inherit from `Smiley` and implement `draw_eyes()` and `draw_mouth()`. `draw_eyes()` is identical for both classes.
   >
3. What difference stands out the most to you and why?
   > The absence of `Blinkable` as parent class of `Sad`, as sad faces deserve the right to use their eyelids too.
   >
4. How does this difference affect the functionality of these classes
   > This means it's not required to provide to override the abstract method `blink()`.
   >

### Where is the Sense(Hat) in the code?

1. Which class(es) utilize the functionality of the SenseHat?
   > `Smiley` is the only class to use it directly, though each of its child classes refer to it indirectly via inheritance.
   >
2. Which of these classes directly interact with the SenseHat functionalities?
   > Just `Smiley`.
   >
3. Discuss the hiding of the SenseHAT in terms of encapsulation (100-200 Words)
   > By referring to the SenseHAT only in the `Smiley` class, the hardware interface is encapsulated, interaction with and access to the class is simplified and protected.
   >

### Sad Smileys Can’t Blink (Or Can They?)

Unlike the `Happy` smiley, the current implementation of the `Sad` smiley does not possess the ability to blink. Let's first explore how blinking has been implemented in the Happy Smiley by examining the blink() method, which takes one argument that determines the duration of the blink.

**Understanding Blink Mechanism:**

1. Does the code's author believe that every `Smiley` should be able to blink? Explain.

   > No, as `blink()` is only a required method of `Blinkable`, of which `Happy` is the only child class.
   >

2. For those smileys that blink, does the author expect them to blink in the same way? Explain.

   > No, as the `blink()` method defined in `Blinkable` uses `@abstractmethod`, requiring its children to implement overrides. Even if it were called with `super`, the abstract method doesn't do anything.
   >

3. Referring to the implementation of blink in the Happy and Sad Smiley classes, give a brief explanation of what polymorphism is.

   > Polymorphism refers, in this case, to the capacity for a class to provide a single interface to objects of different types (`happy`, `sad`) that are subclasses of a common superclass (such as `Blinkable`). `blink` can be called for any class instance of any type that inherits from `Blinkable`.
   >

4. How is inheritance used in the blink method, and why is it important for polymorphism?

   > `sad` is required to define an override for `blink()`, as it inherits from the `Blinkable` abstract base class. Inheritance is the means by which polymorphism is achieved (for subclasses of `Blinkable`)?
   >
**1. Implement Blink in Sad Class:**

- Create a new method called `blink` within the Sad class. Ensure you use the same method signature as in the Happy class:

```python
   def blink(self, delay=0.25):
      pass  # Replace 'pass' with your implementation
```

1. **Code Implementation:** Implement the code that allows the Sad smiley to blink. Use the implementation from the Happy Smiley as a reference. Ensure your new method functions similarly by controlling the blink duration through the `delay` argument.

2. **Testing the Implementation:**

- Test the new blink functionality on your Raspberry Pi or within the Python classes provided. You might need to adjust the `main.py` script to incorporate Sad Smiley's new blinking capability.

Include a screenshot of the sad smiley or the modified `main.py`:

![alt text](image.png)

- Observe and document the Sad smiley as it blinks its eyes. Describe any adjustments or issues encountered during implementation.

  > I don't know why, but the emulator refuses to sleep for less than a second, including in `blink()`.

  ### If It Walks Like a Duck…

  Previously, you implemented the blink functionality for the Sad smiley without utilizing the class `Blinkable`. Assuming you did not use `Blinkable` (even if you actually did), consider how the Sad smiley could blink similarly to the Happy smiley without this specific class.

  1. **Class Type Analysis:** What kind of class is `Blinkable`? Inspect its superclass for clues about its classification.

     > It's an abstract base class.

  2. **Class Implementation:** `Blinkable` is a class intended to be implemented by other classes. What generic term describes this kind of class, which is designed for implementation by others? **Clue**: Notice the lack of any concrete implementation and the naming convention.

      > 'Interface'.

  3. **OO Principle Identification:** Regarding your answer to question (2), which Object-Oriented (OO) principle does this represent? Choose from the following and justify your answer in 1-2 sentences: Abstraction, Polymorphism, Inheritance, Encapsulation.

      > Abstraction, as it exposes a function without specifying how it should be implemented: allows different classes to provide their own implementations without sharing internal details.

  4. **Implementation Flexibility:** Explain why you could grant the Sad Smiley a blinking feature similar to the Happy Smiley's implementation, even without directly using `Blinkable`.

      > The abstract method `blink()` doesn't define the method, but establishes the requirement for an overriding method with a matching signature. `blink` can be implemented without `Blinkable` requiring it.

  5. **Concept and Language Specificity:** In relation to your response to question (4), what is this capability known as, and why is it feasible in Python and many other dynamically typed languages but not in most statically typed programming languages like C#? **Clue** This concept is hinted at in the title of this section.

  > Duck typing: Python doesn't care about the Smiley object's actual type — even without inheriting from `Blinkable`, if a `blink()` method is defined with a matching signature, it can be called. This is because Python is dynamically typed — that is, type checks are completed at runtime, not compile at compile time, meaning objects are assessed by their methods/attributes/properties (not their declared class) as to whether they behave as expected.
  > In a statically-typed language, type checks are completed at compile time, and interfaces implemented in a class must be explicitly declared (if `Sad` doesn't implement the `Blinkable` interface, it can't be passed where that interface is expected, even if a `blink()` method is defined).

  ***

  ## Refactoring

  ### Does a Smiley Have to Be Yellow?

  While our current implementation ~~predominantly~~ features yellow smileys, emotional expressions like sickness or anger typically utilize colors like green, red, or orange. We'll explore the feasibility of integrating these colors into our smileys.

  1. **Defined Colors and Their Location:**

     1. Which colors are defined and in which class(es)?
        > `Smiley` defines `WHITE`, `GREEN`, `RED`, `YELLOW`, and `BLANK`.
           1. What type of variables hold these colors? Are the values expected to change during the program's execution? Explain your answer.
              > Colour data is stored as tuples, declared as constants—they are not expected to change.

     2. Add the color blue to the appropriate class using the appropriate format and values.

  2. **Usage of Color Variables:**

     1. In which classes are the color variables used?
        > `Smiley`, and `Happy` and `Sad`, where `BLANK` is used for drawing mouth and eyes.

  3. **Simple Method to Change Colors:**
  4. What is the easiest way you can think to change the smileys to green? Easiest, not necessarily the best!
     > To change the definition of `YELLOW` to `(0, 255, 0)`.

  Here's a revised version of the "Flexible Colors – Step 1" section for the smiley project, incorporating your specifications for formatting and content updates:

  ### Flexible Colors – Step 1

  Changing the color of the smileys once is straightforward, but it isn't very flexible. To facilitate various colors for smileys, it is advisable not to hardcode values in any class. This approach was identified earlier as a necessary change. Let's start by removing the built-in assumptions about color in our classes.

  1. **Add a method called `complexion` to the `Smiley` class:** Implement this instance method to return `self.YELLOW`. Using the term "complexion" instead of "color" provides a more abstract terminology that focuses on the meaning rather than implementation.

  2. **Refactor subclasses to use the `complexion` method:** Modify any subclass that directly accesses the color variable to instead utilize the new `complexion` method. This ensures that color handling is centralized and can be easily modified in the future.

  3. **Determine the applicable Object-Oriented principle:** Consider whether Abstraction, Polymorphism, Inheritance, or Encapsulation best applies to the modifications made in this step.
      > Abstraction, as the user doesn't need to consider how `complexion` is implemented.

  4. **Verify the implementation:** Ensure that the modifications function as expected. The smileys should still display in yellow, confirming that the new method correctly replaces the direct color references.

  This step is crucial for setting up a more flexible system for color management in the smiley display logic, allowing for easy adjustments and extensions in the future.

  ### Flexible Colors – Step 2

  Having removed the hardcoded color values, we now enhance the base class to support dynamic color assignments more effectively.

  1. **Modify the `__init__()` method in the `Smiley` class:** Introduce a default argument named `complexion` and assign `YELLOW` as its default value. This allows the instantiation of smileys with customizable colors.

  2. **Introduce a new instance variable:** Create a variable called `my_complexion` and assign the `complexion` parameter to it. This step ensures that each smiley instance can maintain its own color state.

  3. **Rationale for `my_complexion`:** Using a distinct instance variable like `my_complexion` avoids potential conflicts with the method parameter names and clarifies that it is an attribute specific to the object.

  4. **Bulk rename:** We want to update our grid to use the value of complexion, but we have so many `Y`s in the grid. Use your IDE's refactoring tool to rename all instances of the **symbol** `Y` to `X`. Where `X` is the value of the `complexion` variable. Include a screenshot evidencing you have found the correct refactor tool and the changes made.

      ![bulk rename](<Screenshot 2025-06-16 at 14.26.39-1.png>)

  5. **Update the `complexion` method:** Adjust this method to return `self.my_complexion`, ensuring that whatever color is assigned during instantiation is what the smiley displays.

  6. **Verification:** Run the updated code to confirm that Smileys still defaults to yellow unless specified otherwise.

  ### Flexible Colors – Step 3

  With the foundational changes in place, it's now possible to implement varied smiley colors for different emotional expressions.

  1. **Adjust the `Sad` class initialization:** In the `Sad` class's initializer method, change the superclass call to include the `complexion` argument with the value `self.BLUE`, as shown:

     ```python
     super().__init__(complexion=self.BLUE)
     ```

  2. **Test color functionality for the Sad smiley:** Execute the program to verify that the Sad smiley now appears blue.

  3. **Ensure the Happy smiley remains yellow:** Confirm that changes to the Sad smiley do not affect the default color of the Happy smiley, which should still display in yellow.

  4. **Design and Implement An Angry Smiley:** Create an Angry smiley class that inherits from the `Smiley` class. Set the color of the Angry smiley to red by passing `self.RED` as the `complexion` argument in the superclass call.

  ***
