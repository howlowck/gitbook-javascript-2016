# Virtual DOM

Virtual DOM is one of those things that at first seems like a bad idea but actually turns out to be a game-changer.

The idea of React is that whenever there is a new state, React rerenders EVERYTHING!

If this were to be done on the actual DOM, the react app would be unusable.

So, what React does is keep track of the current DOM tree and when a state changes, renders out a virtual DOM tree and diffs the current DOM tree vs the new virtual DOM, then only changes the content or attributes that have changed or add new elements.

You can learn more about the virtual dom by watching this video:
{%youtube%}https://www.youtube.com/watch?v=-DX3vJiqxm4{%endyoutube%}
