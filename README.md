# RailsAdminGrid

RailsAdminGrid is a custom collection action for RailsAdmin that displays objects in a grid with thumbnails. It provides an alternative to the default list view provided in RailsAdmin.

## Configuration

### Global

You must add the custom action to the list of actions in your global RailsAdmin configuration. The default, with RailsAdminGrid added, looks like this:

```ruby
# config/initializers/rails_admin.rb
RailsAdmin.config do |config|
  config.actions do
    # root actions
    dashboard                     # mandatory
    # collection actions 
    index                         # mandatory
    new
    export
    history_index
    bulk_delete
    # member actions
    show
    edit
    delete
    history_show
    show_in_app

    grid                          # RailsAdminGrid
  end
end
```

Since RailsAdminGrid works best for displaying models with an associated picture, it may not be desirable to use on every model. You can restrict the models for which the action is available using the steps described [here](https://github.com/sferik/rails_admin/wiki/Actions#per-model-basis).

### Model

To configure RailsAdminGrid's behavior on a specific model, you must include a `grid` block in your model configuration, as such:

```ruby
rails_admin do
  grid do
    thumbnail_method do
      :thumb
    end
  end
end
```

The only information RailsAdmin requires to function properly is a `thumbnail_method`, a method which it will use to retrieve the corresponding thumbnail for the object. It also supports many of the applicable options used in the default list action ([see more](https://github.com/sferik/rails_admin/wiki/List)).