# blog


### Personal notes on how setup things

#### Install things

```bash
sudo apt install ruby ruby-dev
sudo gem install bundler jekyll

bundle install

```

If it fails with this error:

```
find_spec_for_exe': can't find gem bundler (>= 0.a) with executable bundle
```

Just delete the `Gemfile.lock` and run `bundle install` again.


#### Serve