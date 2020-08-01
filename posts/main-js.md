---
title: main.js
date: 2020-08-02
tags:
layout: layouts/post.njk
---

```js
/*
export const newFirkin = () => {

    const v = [] // values
    const vds = []
    const tgs = []
    return {
        set: (n,v) => {}
    }
}
*/

function Firkin(c) {

    let t = this;

    if (c) // config
    {
        if (c.mut==false) t.mut = false; // allow mutation
        if (c.trc==true) t.trc = true;   // stack trace on error
    }

    t.err = function(msg)
    {
        if (t.trc) console.trace(msg);
        else console.log(msg);
    }

    t.v = {};   // values
    t.vds = {}; // validation
    t.tgs = {}; // triggers
    t.fs = [];  // functions

    this.set = function(n,v)
    {
        if (t.mut==false) { t.err('cannot mutate'); }
        else
        {
            let ok = true;
            if (t.vds[n]) t.vds[n].forEach( f => { 
                if (!f(v)) {
                    ok = false; 
                    t.err('validation failed: '+f.toString());
                }
            });
            if (ok) {
                t.v[n] = v;
                if (t.tgs[n]) t.tgs[n].forEach( (f) => f(v) ); // run triggers
                t.fs.forEach( ff => {

                    ff.i.forEach( i => {

                        //if (i==n) ff.f
                    })
                });
            }
        }
    }

    t.get = function(n)
    {
        return t.v[n];
    }

    t.vld = function(n, f)
    {
        if (!t.vds[n]) t.vds[n] = [];
        t.vds[n].push(f);
    }

    t.trg = function(n, f)
    {
        if (!t.tgs[n]) t.tgs[n] = [];
        t.tgs[n].push(f);
    }

    t.fnc = function(i, o, f)
    {
        t.fs.push({i:i, o:o, f:f});
    }
}

let a = new Firkin({mut: false});
let b = new Firkin;

b.vld('x', (x) => x < 10 );
b.vld('y', (y) => typeof y == 'number' );

b.trg('z', (z) => console.log('got z =', z) );

a.fnc( ['x','y'], ['z'], (x,y) => ({'z': x + y}) );

a.set('x', 10);
b.set('x', 20);
b.set('y', 'hello');
//b.set('z', 123.0);

console.log('ax =',a.get('x'));
console.log('bx =',b.get('x'));
```