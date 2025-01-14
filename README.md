# WillFilter

will_filter is a Rails engine plugin that provides a GUI for filtering your ActiveRecord models.

## Preamble

If you ever had to build an admin tool for your web site that displayed a list of objects that can be filtered using
various criteria, this plugin will make your life easier. Adding a filtered page can now be
a matter of adding two lines of code - one to your controller and one to your view. See examples below.

## Installation Instructions

Add the following gems to your Gemfile:

```Gemfile
gem 'will_filter'
gem 'kaminari'
```

And run:

```sh
$ bundle
```

To configure and initialize will_filter engine, run the following commands:

```sh
$ rails generate will_filter
$ rake db:migrate
```

At the top of your routes.rb file, add the following line:

```ruby
mount WillFilter::Engine => "/will_filter"
```

## Examples

To add a filtered result-set to your controller use the following method call:

```ruby
class UsersController < ApplicationController

    def index
      @users = User.filter(:params => params)
    end

end
```

Note: 'User' is a Rails ActiveRecord model

Now all you have to do is create a view for this action and add the following tag where you want the filter to be rendered:

```erb
<%= will_filter_tag(@users) %>
```

And optionally you can do (for results table):

```erb
<%= will_filter_table_tag(@users) %>
```

That's it. This will render a filter box with various conditions, operators and values for the model object you selected.

## Documentation

Please read the following document to learn more about filter customization:

https://github.com/berk/will_filter/wiki/Customizing-Filters

Please read the following document to learn more about table tag customization:

https://github.com/berk/will_filter/wiki/Customizing-Table-View

## Dummy Application

This plugin comes with a dummy test project. To try out some of the examples, run the following commands:

```sh
$ git clone git://github.com/berk/will_filter.git
$ cd will_filter/test/dummy
$ rake db:migrate
$ rake samples:init
$ rails server
```

Open your browser and point to:

```
http://localhost:3000
```

If you have any questions, comments or suggestions, email me at <theiceberk@gmail.com>

## Authors and credits

Authors:: Michael Berkovich
