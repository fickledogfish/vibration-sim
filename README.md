# Mass-Spring-Damper Simulator

<p align="center">
  <img src="https://github.com/fickledogfish/vibration-sim/blob/master/animation.gif?raw=true" alt="Animation"/>
</p>

In vibration theory, this is the first studied system, for many reasons. This
system is simple enough for didactic demonstration in classes and complex enough
to show every basic concept needed for advanced studies.

So, to help students visualize this basic concepts and to teach me a little more
Clojure, I coded this project in my free time. I also thought it would be cool
to include it in my course completion assignment to complement some basic
explanations.

# The Project

Using Clojure, a little bit of [play-clj][play-clj], and a lot of free time and
will of learning a new programming language, I put together a simple animation
to demonstrate the response of the system for diferent levels of damping.

This project was built using the [Leiningen][leiningen] project automation tool,
with the `play-clj` template and the [Claypoole][claypoole] library, so these
are the only dependencies (though, because of the way Leiningen handles
dependencies, you probably won't worry about it).

Also, please note there are no test functions. This is to be modified later.
Maybe.

# Usage

## Running The Program

Simply launch the program (pre-compiled standalone `.jar` lives in the `target/`
folder), as any Java file

```
java -jar path_to_jar_file/vibration-sim-1.2.2-standalone.jar
```

(changing `path_to_jar_file` to the actual path of the downloaded file), and use
any keys listed in the section below. If you want to clone the whole project, it
is pretty much standart for git repositories. The command

```
git clone https://github.com/fickledogfish/vibration-sim
```

will do the trick. To run with Leiningen, simply `lein run` on the cloned
folder (as of any Leiningen project, dependencies are downloaded in the first
run). To compile and generate the `.jar` file, simply run `lein uberjar`.

_Note_: if you change the screen size (variables `screen-dim-x` and
`screen-dim-y` defined in `src-common/vibration_sim/constants.clj`), you have to
make sure `src/vibration_sim/core/desktop_launcher.clj` is recompiled. I
actually don't know how to force it in `lein run`, so I just recompile the whole
project with `lein uberjar`. Please let me know of a better method.

## Vibration Modes

This simulation presents an animated representation for the really basic MSD
responses, assuming the system is not affected by external forces. The program
will automatically decide wich function to use based on the input given by the
user. The possibilities are:

1. *undamped system*: the system is reduced to the mass-spring, in
    which the mass oscilates forever, and amplitude of the movemnt remains
    constant;
2. *low-damped system*: damping means the system will lose energy
    over time, so the mass will oscilate, but its amplitude will reduce over
    time, untill the system comes to a stop;
3. *high-damped system*: high damping means the system will not
    oscilate, instead, it will return as fast as possible to the equilibrium
    position.

To quit the program, there is also the <kbd>q</kbd> shortcut.

Also, note that pressing any key (except <kbd>q</kbd>, of course) will reset the
time to zero, thus restarting the animation with the previous data. To start the
animation with the new values, simply press the helpfull <kbd>Apply</kbd> button.

# Bug Reports, Suggestions, Pull Requests, ...

Please read CONTRIBUTING.md file.

# TODOS

## Improvements

* [ ] add [expectations][expectations] and [lein-autoexpect][lein-autoexpect] as
    dependencies;
* [ ] write test functions using expectations and lein-autoexpect.

## New features

* [ ] adjust the sliders range and step for better animations;
* [ ] add forced vibrations and resonance;
* [ ] adjust the pressed button image;
* [x] add modifiers for the spring and damper constants, so the
    program can be run with multiple values (text input from the user
    is preferable);
* [x] show small marks at previous positions of the mass;
* [x] make the label at the botton show the current time.

## Known bugs

No bug is known at the moment.

# Changelog

* 2015-07-16: **2.0.0**
  * small change in the creation of the sliders;
  * correction of the movement equations;
  * correction of the table (sliders/labels/buttons) location;
  * changed documentation to reflect the new functionality.
* 2015-07-03: **1.2.4**
  * small correction in the Changelog section of the README.md file;
  * add a simple animation for demonstration.
* 2015-06-08: **1.2.3**
  * corrected line endings of the files;
  * contrubition instructions;
  * created development branch.
* 2015-05-13: **1.2.2**
  * changed some java-based mathematical functions to macros;
  * corrected some function contracts;
  * changed some organization of the code.
* 2015-04-25: **1.2.1**
  * add claypoole as a dependency;
  * movement functions now run in parallel;
  * "q" now kill the threadpool and exits the program.
* 2015-04-21: **1.2.0**
  * took a while to figure it out, but we have the timer printed on the
      screen;
  * blue dots now follow the mass, showing the plot of the movement equation;
  * the dots are removed from the animation as soon as they leave the screen;
  * the dots are also removed with any keypress, so re-starting any animation
      actually re-starts everything.
* 2015-04-20: **1.1.0**
  * first working version of the program;
  * the mass-rectangle-thingy changes movement type with certain keys;
  * any key resets the time (making restart easier);
  * resized the window (makes more sense to me as it is).

[play-clj]: https://github.com/oakes/play-clj
[leiningen]: http://leiningen.org/
[expectations]: https://github.com/jaycfields/expectations
[lein-autoexpect]: https://github.com/jakemcc/lein-autoexpect
[claypoole]: https://github.com/TheClimateCorporation/claypoole
