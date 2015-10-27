{exec} = require 'child_process'
fs = require 'fs'

extensions = [
  "pdf"
  "html"
]

option '-t', '--type [EXTENSION]', "type of file to generate #{extensions}, leave blank for pdf"
option '-f', '--file [NAME]', "name of md file to generate for, leave blank for all"

run = (string, opts={}) ->
  exec string, (err, stdout, stderr) ->
    console.log stdout if stdout
    console.log stderr if stderr unless opts.silent
    console.log err if err unless opts.silent

generate = (filename, filetype) ->
  console.log "generating #{filename}.#{filetype}"
  run "pandoc #{filename}.md -V geometry:margin=1in -s -o #{filename}.#{filetype}"

allFiles = (callback) ->
  fs.readdir __dirname, (err, files) ->
    console.log err if err
    callback(f[0...-3]) for f in files when f[-3..-1] is '.md' and f isnt 'README.md'

task 'generate', "generate files", (options) ->
  options.type = 'pdf' unless options.type in extensions
  if options.file
    generate options.file, options.type
  else
    allFiles (file) -> generate file, options.type

task 'clean', "remove all generated files", ->
  # extensions = ["pdf", "html"]
  run "rm *.#{ext}", silent: true for ext in extensions
