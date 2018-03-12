# Installing Neovim with Anaconda/Miniconda python

I use Ananconda/Miniconda on all systems. I typically therefore link libraries against the most recent versions of python provided through these.

Installing Neovim with `make CMAKE_BUILD_TYPE=RelWithDebInfo` often causes issues like the following:

```
/apps/skylake/software/core/anaconda3/5.0.1/bin/libtool: line 10548: /apps/skylake/software/core/anaconda3/5.0.1/bin/x86_64-conda_cos6-linux-gnu-cc: No such file or directory
```

This is because Unilibium uses libtool which is provided by Anaconda by default, but points to [their custom compiler tools](https://conda.io/docs/user-guide/tasks/build-packages/compiler-tools.html).  The solution to this is to make sure that libtool is installed in the current conda environment:

```
conda install libtool
```

The Neovim build should then work flawlesly.

**Side note**: I think the Neovim build system (cmake with heavy use of `ExternalProject_Add` + a make wrapper) is THE best I have seen for a c/c++ project.  I should study this more and use it as a template for my projects wherever appropriate.
