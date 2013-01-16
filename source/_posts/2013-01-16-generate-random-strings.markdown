---
layout: post
title: "Generate Random Strings in the Shell"
date: 2013-01-16 10:19
comments: true
categories: [Ruby, Randomness]
---

Ruby 1.9.3 has a handy standard library called [SecureRandom](http://www.ruby-doc.org/stdlib-1.9.3/libdoc/securerandom/rdoc/SecureRandom.html) that you can use to generate random base64 and hex encoded strings of varying length.  

```ruby
p SecureRandom.base64 #=> "BSosm7R3qpzxb+julERofA=="
p SecureRandom.hex #=> "0748834731ab0c35efd44610161f0ee3"
```

If you are already using Ruby, and you need to generate random strings, go ahead and use SecureRandom.  But what if you aren't using Ruby? Well you don't have to go searching for a similar library in your language, because SecureRandom is built on top of [OpenSSL](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&cad=rja&ved=0CDMQFjAA&url=http%3A%2F%2Fwww.openssl.org%2F&ei=58X2UNZ1i_r2BP63gbAP&usg=AFQjCNGtJbR6MAQZ3JmaMST4e19Co9b6PA&bvm=bv.41018144,d.eWU), and if you have Mac OS X or linux, chances are you already have access to the `openssl` command line tool. 

```sh
$ openssl rand -base64 16
t1nkx6lFae7s7dyGDuzgiw==
$ openssl rand -hex 16
809420e83e80ebae689e814b1861bf5c
```

This way you can quickly generate secure random strings without worrying about running Ruby.
