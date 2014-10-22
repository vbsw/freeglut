# freeglut

## Abstract
This is freeglut binding for the programming language Go. It works on linux.

## Installation

	go get github.com/vitalibaumtrok/freeglut
	go install github.com/vitalibaumtrok/freeglut

To update the package type

	go get -u github.com/vitalibaumtrok/freeglut

_Note: You need the programming language Go and git to run these commands._

## Development
Programming language Go is used. This binding isn't finished.

The reference for the freeglut functions is taken from <http://freeglut.sourceforge.net/docs/api.php>



## Example
	package main

	import (
		glut "github.com/vitalibaumtrok/freeglut"
	)

	func main() {
		glut.Init()
		glut.InitDisplayMode(glut.SINGLE | glut.RGBA)
		glut.InitWindowSize(640, 480)
		glut.CreateWindow("Testing GLUT binding for Go");
		glut.ReshapeFunc(reshape)
		glut.DisplayFunc(display)
		glut.KeyboardFunc(keyboard)
		glut.MainLoop()
	}

	func reshape(width, height int) {
		println("reshape")
	}

	func display() {
		println("display")
	}

	func keyboard(key uint8, x, y int) {
		if key==27 { // escape
			glut.DestroyWindow(glut.GetWindow())
		} else {
			if (glut.GetModifiers() & glut.ACTIVE_CTRL) > 0 {
				println("key pressed: ctrl +", key)
			} else {
				println("key pressed:", key)
			}
		}
	}

## Copyright
Copyright 2014 Vitali Baumtrok

This program is distributed under the terms of the Boost Software License,
Version 1.0. (See accompanying file LICENSE_1_0.txt or copy
at http://www.boost.org/LICENSE_1_0.txt)
