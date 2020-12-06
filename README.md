# chain-ops-python
Simple chaining of operations (a.k.a. pipe operator) in python

There is no need for an elaborate module or fancy operator to do this.  
It's a very simple function and looks perfectly clean to use. Here it is:

    def chain( Accumulant, *Functions_list ):
        for f in Functions_list: Accumulant = f( Accumulant )
        return Accumulant

That's it!
Feel free to place it in a module and import it if you really have to.

Example:

    add      = lambda x: lambda y: x + y
    addlist  = lambda x: lambda l: [ add(x)(i) for i in l]
    list2chr = lambda l: [ chr(i) for i in l ]
    joinstr  = lambda j: lambda s: j.join(s)

    L = [4,1,8,8,11,-68,19,11,14,8,0,-67]

    chain( L
           , addlist(100)
           , list2chr
           , joinstr("")
           , str.lower
           , str.split   )

    # outputs: ['hello', 'world!']

See also: [Simple chaining of operations (a.k.a. pipe operator) in octave](https://github.com/tpapastylianou/chain-ops-octave)

