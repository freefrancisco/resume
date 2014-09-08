{exec} = require 'child_process'

run = (string, opts={}) ->
  exec string, (err, stdout, stderr) ->
    console.log stdout if stdout
    console.log stderr if stderr unless opts.silent
    console.log err if err unless opts.silent

extensions = [
  "pdf"
  "html"
]

option '-t', '--type [EXTENSION]', "type of file to generate #{extensions}"


task 'generate', "generate a resume file type given by -t", (options) ->
  type = options.type
  switch
    when type in extensions
      run "pandoc resume.md -V geometry:margin=1in -s -o resume.#{type}"
    when type? and type not in extensions
      console.log "the only valid types after -t are [#{extensions.join(', ')}]"
    else
      console.log """usage: cake -t ext generate
      where ext is any of [#{extensions.join(', ')}]"""

task 'clean', "remove all generated resume files", ->
  # extensions = ["pdf", "html"]
  run "rm resume.#{ext}", silent: true for ext in extensions
