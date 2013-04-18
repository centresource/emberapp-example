To run this, you need both ruby/bundler and node/npm, because the tech is so young
that now real definitive tooling yet exists for it. Anyway, you can use
the Gemfile to compile and build all the necessary gems, and - in
addition - you'll need to install the npm package "ember-precompile"
directroy from github, since the author hasn't bothered to update the
npm repository in god knows how long. Run the following command

  npm install -g https://github.com/gabrielgrant/node-ember-precompile/archive/master.tar.gz

Once all that's installed and ready, you can just run

  guard

and that'll kick stuff off. Jasmine is being used for JS testing, and
the jasmine server can be activated with

  rake jasmine
