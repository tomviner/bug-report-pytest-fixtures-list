# bug-report-pytest-fixtures-list
Example project to show incorrect listing of `py.test --fixtures`

```
(pytest-fixture-find)~/dev/pytest-fixture-find$ find -name conftest.py
./project/app1/tests/conftest.py
./project/app2/tests/conftest.py

(pytest-fixture-find)~/dev/pytest-fixture-find$ ack-grep --py --context 1 "def fix"
project/app1/tests/conftest.py
3-@pytest.fixture
4:def fixy1():
5-    pass

project/app2/tests/conftest.py
3-@pytest.fixture
4:def fixy2():
5-    pass

$ py.test --fixtures --traceconfig
PLUGIN registered: <_pytest.python.FixtureManager instance at 0x7f2af6b43440>
=============== test session starts ===============
platform linux2 -- Python 2.7.8 -- py-1.4.28 -- pytest-2.7.1
using: pytest-2.7.1 pylib-1.4.28
active plugins:
    helpconfig          : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/helpconfig.pyc
    pytestconfig        : <_pytest.config.Config object at 0x7f2af9296550>
    runner              : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/runner.pyc
    unittest            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/unittest.pyc
    pastebin            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/pastebin.pyc
    skipping            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/skipping.pyc
    genscript           : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/genscript.pyc
    session             : <Session 'pytest-fixture-find'>
    tmpdir              : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/tmpdir.pyc
    capture             : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/capture.pyc
    terminalreporter    : <_pytest.terminal.TerminalReporter instance at 0x7f2af6db0b00>
    assertion           : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/assertion/__init__.pyc
    mark                : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/mark.pyc
    terminal            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/terminal.pyc
    main                : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/main.pyc
    nose                : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/nose.pyc
    python              : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/python.pyc
    recwarn             : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/recwarn.pyc
    funcmanage          : <_pytest.python.FixtureManager instance at 0x7f2af6b43440>
    monkeypatch         : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/monkeypatch.pyc
    resultlog           : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/resultlog.pyc
    capturemanager      : <_pytest.capture.CaptureManager instance at 0x7f2af6db1488>
    junitxml            : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/junitxml.pyc
    doctest             : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/doctest.pyc
    pdb                 : /home/me/.virtualenvs/pytest-fixture-find/local/lib/python2.7/site-packages/_pytest/pdb.pyc
    139822545592848     : <_pytest.config.PytestPluginManager object at 0x7f2af9296210>
rootdir: /home/me/dev/pytest-fixture-find, inifile:
PLUGIN registered: <module 'conftest' from '/home/me/dev/pytest-fixture-find/project/app1/tests/conftest.pyc'>
PLUGIN registered: <module 'conftest' from '/home/me/dev/pytest-fixture-find/project/app2/tests/conftest.pyc'>
collected 2 items
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
fixy1
    project/app1/tests/conftest.py:4: no docstring available

================  in 0.01 seconds ============={}
```

So `fixy1` shows but not `fixy2.`
