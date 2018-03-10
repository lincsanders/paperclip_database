Paperclip Database Storage
==========================

Paperclip Database Storage is an additional storage option for
Paperclip. It gives you the opportunity to store your paperclip binary
file uploads in the database along with all your other data.

Requirements
------------

`paperclip_database` depends on `paperclip`

Installation
------------

Eeeehhhhh it works with rails 5+ now

    gem "paperclip_database", :git => "git://github.com/lincsanders/paperclip_database.git"

Supported Versions
------------------

Supported version are rails >= 3.0 and paperclip version >= 2.3

Quick Start
-----------

There is no quick start. You definitely need to understand how to use
paperclip first.

Usage
-----

You use `paperclip_database` by specifying `database` as storage for
your paperclip and create a migration for the additional database
table.

In your model:

    class User < ActiveRecord::Base
      has_attached_file :avatar,
                        :storage => :database ## This is the essence
                        :styles => { :medium => "300x300>", :thumb => "100x100>" }
    end

There is a migration generator that will create a basic migration for
the extra table.

On the console (rails 3):

    bundle exec ./script/rails generate paperclip_database:migration User avatar

The generated migration should be sufficient, but you may consider
adding additional code to the migration such as `t.timestamps` for
adding standard rails timesstamps or a referential database
constraint, or an index on the foreign key id column. If you add a
refferential constraint with the option `ON DELETE CASCADE`, then you
need to add the option `:cascade_deletion => true` to your paperclip
`has_attached_file` declaration to let PaperclipDatabase know that the
Database takes care of it. Otherwise PaperclipDatabase will do the
cascade deletion.

Development
-----------

To start develop, please download the source code

    git clone git://github.com/lincsanders/paperclip_database.git

When downloaded, you can start issuing the commands like

    bundle install
    bundle exec appraisal clean
    bundle exec appraisal generate
    bundle exec appraisal install
    bundle exec appraisal rake

Or you can see what other options are there:

    bundle exec rake -T


History
-------

Forker from https://github.com/softace/paperclip_database


Copyright
---------

Copyright (c) 2018 Lincoln Sanderson. See LICENSE.txt for
further details.
