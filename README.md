# bug-report-pytest-fixtures-list
Example project to show incorrect listing of `py.test --fixtures`

```
(pytest-fixture-find)~/dev/pytest-fixture-find$ find -name conftest.py
./app3/tests/conftest.py
./conftest.py
./project/app1/tests/conftest.py
./project/conftest.py
./project/app2/tests/conftest.py

(pytest-fixture-find)~/dev/pytest-fixture-find$ ack-grep --py --context 1 "def fix"
app3/tests/conftest.py
3-@pytest.fixture
4:def fixy3():
5-    pass

conftest.py
3-@pytest.fixture
4:def fixy4():
5-    pass

project/app1/tests/conftest.py
3-@pytest.fixture
4:def fixy1():
5-    pass

project/conftest.py
3-@pytest.fixture
4:def fixy5():
5-    pass

project/app2/tests/conftest.py
3-@pytest.fixture
4:def fixy2():
5-    pass

$ py.test --fixtures --traceconfig
PLUGIN registered: <_pytest.python.FixtureManager instance at 0x7f8f0bcb46c8>
=============== test session starts ===============
platform linux2 -- Python 2.7.9 -- py-1.4.28 -- pytest-2.7.1
using: pytest-2.7.1 pylib-1.4.28
active plugins:
    helpconfig          : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/helpconfig.pyc
    pytestconfig        : <_pytest.config.Config object at 0x7f8f0daddd10>
    runner              : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/runner.pyc
    unittest            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/unittest.pyc
    pastebin            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/pastebin.pyc
    skipping            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/skipping.pyc
    genscript           : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/genscript.pyc
    session             : <Session 'bug-report-pytest-fixtures-list'>
    tmpdir              : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/tmpdir.pyc
    capture             : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/capture.pyc
    terminalreporter    : <_pytest.terminal.TerminalReporter instance at 0x7f8f0bcca290>
    assertion           : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/assertion/__init__.pyc
    mark                : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/mark.pyc
    terminal            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/terminal.pyc
    main                : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/main.pyc
    nose                : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/nose.pyc
    python              : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/python.pyc
    recwarn             : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/recwarn.pyc
    funcmanage          : <_pytest.python.FixtureManager instance at 0x7f8f0bcb46c8>
    monkeypatch         : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/monkeypatch.pyc
    resultlog           : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/resultlog.pyc
    capturemanager      : <_pytest.capture.CaptureManager instance at 0x7f8f0bfac7a0>
    140252386548176     : <_pytest.config.PytestPluginManager object at 0x7f8f0dadd9d0>
    junitxml            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/junitxml.pyc
    doctest             : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/doctest.pyc
    /home/me/Dropbox/DellXPS-backup/dev/pytest-fixture-find/conftest.pyc: /home/me/Dropbox/DellXPS-backup/dev/pytest-fixture-find/conftest.pyc
    pdb                 : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/pdb.pyc
rootdir: /home/me/Dropbox/DellXPS-backup/dev/pytest-fixture-find, inifile:
PLUGIN registered: <module 'conftest' from '/home/me/Dropbox/DellXPS-backup/dev/pytest-fixture-find/project/conftest.pyc'>
PLUGIN registered: <module 'conftest' from '/home/me/Dropbox/DellXPS-backup/dev/pytest-fixture-find/app3/tests/conftest.pyc'>
PLUGIN registered: <module 'conftest' from '/home/me/Dropbox/DellXPS-backup/dev/pytest-fixture-find/project/app1/tests/conftest.pyc'>
PLUGIN registered: <module 'conftest' from '/home/me/Dropbox/DellXPS-backup/dev/pytest-fixture-find/project/app2/tests/conftest.pyc'>
collected 3 items
capsys
    enables capturing of writes to sys.stdout/sys.stderr and makes
    captured output available via ``capsys.readouterr()`` method calls
    which return a ``(out, err)`` tuple.
capfd
    enables capturing of writes to file descriptors 1 and 2 and makes
    captured output available via ``capfd.readouterr()`` method calls
    which return a ``(out, err)`` tuple.
monkeypatch
    The returned ``monkeypatch`` funcarg provides these
    helper methods to modify objects, dictionaries or os.environ::

    monkeypatch.setattr(obj, name, value, raising=True)
    monkeypatch.delattr(obj, name, raising=True)
    monkeypatch.setitem(mapping, name, value)
    monkeypatch.delitem(obj, name, raising=True)
    monkeypatch.setenv(name, value, prepend=False)
    monkeypatch.delenv(name, value, raising=True)
    monkeypatch.syspath_prepend(path)
    monkeypatch.chdir(path)

    All modifications will be undone after the requesting
    test function has finished. The ``raising``
    parameter determines if a KeyError or AttributeError
    will be raised if the set/deletion operation has no target.
pytestconfig
    the pytest config object with access to command line opts.
recwarn
    Return a WarningsRecorder instance that provides these methods:

    * ``pop(category=None)``: return last warning matching the category.
    * ``clear()``: clear list of warnings

    See http://docs.python.org/library/warnings.html for information
    on warning categories.
tmpdir
    return a temporary directory path object
    which is unique to each test function invocation,
    created as a sub directory of the base temporary
    directory.  The returned object is a `py.path.local`_
    path object.

------------- fixtures defined from conftest --------------
fixy4
    conftest.py:4: no docstring available
fixy3
    app3/tests/conftest.py:4: no docstring available

================  in 0.02 seconds =============
```

So you see `fixy3` & `fixy4` but not 1, 2 & 5