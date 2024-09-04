# session-10-assignment-shane-rodricks
# Session 8 Assignment - Refactoring Polygons Class into an Iterable
Name: Shane Rodricks
Email: spiderpig27570@gmail.com
Session: 8: Advanced Python Topics

# Project Description
This project focuses on refactoring a sequence-type class, Polygons, into an iterable type by implementing both an iterable and an iterator. The original code defines a Polygon class representing a regular polygon and a Polygons class that stores a collection of polygons. The main goal is to make the Polygons class iterable using Python’s iterator protocol.

# Original Functionality
The original Polygons class was implemented as a sequence type, with the following key features:

# Attributes:
m: The maximum number of polygon sides.
R: The circumradius of the polygons.
Methods:
__getitem__: Provides indexing and slicing to retrieve specific polygons.
__len__: Returns the number of polygons in the collection.
max_efficiency_polygon: Returns the polygon with the highest area-to-perimeter ratio.

# Changes Made (Refactoring into an Iterable)
In this refactoring, I made the following changes:

# Created an Iterator Class:

A new class, PolygonsIterator, was added to implement the iteration logic. This class uses the __next__ method to return the next polygon in the collection and raises StopIteration when there are no more polygons to iterate through.
class PolygonsIterator:
    def __init__(self, polygons):
        self._index = 0
        self._polygons = polygons

    def __iter__(self):
        return self

    def __next__(self):
        if self._index >= len(self._polygons):
            raise StopIteration
        else:
            polygon = self._polygons[self._index]
            self._index += 1
            return polygon

# Updated the Polygons Class to be Iterable:

The Polygons class now implements the __iter__ method, which returns an instance of PolygonsIterator. This makes the Polygons class fully iterable, allowing it to be used in for loops and other iteration contexts.

def __iter__(self):
    return PolygonsIterator(self._polygons)

# Refactored Functionality
Polygons Class:
Can now be iterated over using for loops.
The PolygonsIterator allows the iteration of polygons from 3 sides to m sides.
# Testing
The test suite has been updated to verify the correctness of the refactored iterable implementation. The tests ensure that:

The Polygons class can be iterated over.
Polygons are returned in the correct order during iteration.
The iterator raises StopIteration appropriately at the end of the collection.

Refactored Functionality
Polygons Class:
Can now be iterated over using for loops.
The PolygonsIterator allows the iteration of polygons from 3 sides to m sides.
Testing
The test suite has been updated to verify the correctness of the refactored iterable implementation. The tests ensure that:

The Polygons class can be iterated over.
Polygons are returned in the correct order during iteration.
The iterator raises StopIteration appropriately at the end of the collection.

Example Usage
The Polygons class can now be used in a loop as follows:
polygons = Polygons(6, 5)
for polygon in polygons:
    print(polygon)

This would iterate over polygons with 3 to 6 sides.

# Key Concepts Demonstrated
Iterator Protocol: The separation of iterable and iterator logic into two distinct classes (Polygons and PolygonsIterator) demonstrates the correct use of Python's iterator protocol.
Refactoring: Transforming a sequence type into an iterable class, improving the usability and integration with Python's native iteration tools.