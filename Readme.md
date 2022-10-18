# What is Cookiecutter

> `Cookiecutter` is a CLI tool (Command Line Interface) to create an application boilerplate from a template. It uses a templating system — `Jinja2` — to replace or customize folder and file names, as well as file content.

> Picture Example for Cookiecutter :- 

- [Click Here for the picture](example.png)

# 
## How a Cookiecutter template works

> A Cookiecutter repository template looks something like this:

```sh 
- cookiecutter.json
 — hooks
 | — pre_get_project.py
 | — post_get_project.py
 — [ README.md ]
 — [ CHANGELOG.md ]
 — {{cookiecutter.project_slug}}
 | — < your repository template here >
```
> Let’s see each item in detail:
- `Cookiecutter.json` is the key file in your template. It is a JSON with variables and choices, we will talk about it in the next section.
- `Hooks` are python scripts with rules applicable before and after the repository generation. Personally I use the pre-hook to validate the choices you make and the post-hook to remove undesired files depending on those choices.
- `{{cookiecutter.project_slug}}/< your repository template here >`
Here you will put your repository template with all the structure and content you want to replicate, placing template variables — between double curly brackets {{ }} — and Jinja2 ifs and loops.
- `README.md` and `CHANGELOG.md` are not mandatory, but I really recommend you to have them to explain in detail the choices available in the Json file and to to keep track of the template evolution.
    - Note:- This `Readme` and `Changelog` will not be present in the generated repository, there should be another `Readme` and `Changelog` within `<your repository template>.`

#
## Variables and choices in cookiecutter.json

> To have names and content generated you define different variables in the cookiecutter.json, so you will get prompted for the values you want.

> For each variable you set a default text value, a boolean option or a list of options. Some usual examples:

```sh 
{
  project_name: Project Sample
  project_slug :{{ cookiecutter.project_name.lower().replace(‘ ‘,  ‘_’).replace(‘-’, ‘_’) }}”
  python_version: [“2.7.15”, “3.6.5”]
  some_lib_version: 1.2.1
  initial_version: [“0.1.0rc1”, “1.0.0rc1”]
  use_pytest: true
}
```

#
> Read More 
- [`Project Templates and Cookiecutter`](https://medium.com/worldsensing-techblog/project-templates-and-cookiecutter-6d8f99a06374)

#
> Some templates you can already use

- While researching this topic I’ve compiled a few Cookiecutter templates ready to use or fork. Here’s the list:
    - [`Cookiecutter Python Template`](https://github.com/jacebrowning/template-python)
    - [`Cookiecutter PyPackage Template`](https://github.com/audreyr/cookiecutter-pypackage)    
    - [`Cookiecutter Django Template`](https://github.com/pydanny/cookiecutter-django)
    - [`Cookiecutter Pylibrary Template`](https://github.com/ionelmc/cookiecutter-pylibrary)
    - [`Cookiecutter Flask Template`](https://github.com/sloria/cookiecutter-flask)


# Setup for Cookiecutter

```sh
pip install cookiecutter
cookiecutter <'github_url'>
```
>Simple Demo for creating python templates using cookiecutter:-

```sh
pip install cookiecutter
cookiecutter https://github.com/Diwas2055/cookiecutter_test
```