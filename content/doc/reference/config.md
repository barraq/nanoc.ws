---
title:      "Configuration"
is_dynamic: true
---

## `text_extensions`

A list of file extensions that Nanoc will consider to be textual rather than
binary. If an item with an extension not in this list is found, the file
will be considered as binary.

	#!yaml
	text_extensions: <%= array_to_yaml(Nanoc::Int::Configuration::DEFAULT_CONFIG[:text_extensions]) %>

## `output_dir`

The path to the directory where all generated files will be written to. This
can be an absolute path starting with a slash, but it can also be path
relative to the site directory.

	#!yaml
	output_dir: <%= Nanoc::Int::Configuration::DEFAULT_CONFIG[:output_dir] %>

## `index_filenames`

A list of index filenames, i.e. names of files that will be served by a web
server when a directory is requested. Usually, index files are named
“index.html”, but depending on the web server, this may be something else,
such as “default.htm”. This list is used by Nanoc to generate pretty URLs.

	#!yaml
	index_filenames: <%= array_to_yaml(Nanoc::Int::Configuration::DEFAULT_CONFIG[:index_filenames]) %>

## `enable_output_diff`

Whether or not to generate a diff of the compiled content when compiling a
site. The diff will contain the differences between the compiled content
before and after the last site compilation.

	#!yaml
	enable_output_diff: false

## `prune`

The `prune` section contains options for the [prune](/doc/reference/commands/#prune) command, which deletes stray files from the output directory.

	#!yaml
	prune:
	  auto_prune: true
	  exclude: [ '.git', '.hg', '.svn', 'CVS' ]

When `auto_prune` is true, Nanoc will automatically remove files not managed by Nanoc from the output directory.

The `exclude` option determines which files and directories you want to exclude from pruning. If you version your output directory, you should probably exclude VCS directories such as <span class="filename">.git</span> or <span class="filename">.hg</span>.

## `commands_dirs`

Directories to read commands from. This is useful when you have a set of commands that you want to share between sites.

	#!yaml
	commands_dirs: [ '../shared-commands' ]

## `data_sources`

The data sources contains the definition of the data sources of this site. It is a list of hashes with keys described in the sections below; each array element represents a single data source. For example:

	#!yaml
	data_sources:
	  -
	    type: pentabarf # a custom data source
	    items_root: /conference/

For details, see the <%= link_to_id('/doc/data-sources.*') %> page.

## `string_pattern_type`

Sets the type of string pattern to use. Can be `glob` or `legacy`. See the <%= link_to_id '/doc/identifiers-and-patterns.*' %> page for details.

	#!yaml
	string_pattern_type: glob
