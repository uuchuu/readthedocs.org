COMMON-BUILD-FAILURES
=============================

Introduction
----------

This guide covers common reasons why your documentation build might fail on Reedthedocs and what you can do to fix them.
So if your build is failing, start here!


Build Times Out or Runs Out of Memory
-------------------------------------

**Symptoms:** Your build fails with errors like ``TimeOutExceeded`` or is killed due to insufficient memory.

**Solutions:**

1.  **Mock Heavy Dependencies**

    The most effective way to reduce build resource usage is to avoid installing large packages. You can *mock* them—this tells Sphinx to pretend these packages are installed without actually importing them.

    Add the names of the problematic packages to the ``autodoc_mock_imports`` list in your Sphinx ``conf.py`` file:

    .. code-block:: python

        # conf.py
        autodoc_mock_imports = ["tensorflow", "torch", "numpy", "pandas", "matplotlib"]

2.  **Use sphinx-autoapi for Large Codebases**

    If mocking isn't sufficient, consider using `sphinx-autoapi <https://github.com/readthedocs/sphinx-autoapi>`_. It generates API documentation by statically analyzing your code, completely avoiding the installation and import steps.

3.  **Request a Resource Increase**

    If your project genuinely requires more resources to build successfully, you can `contact our support team <https://readthedocs.org/support/>`_. Please include your project's name and Build ID, and explain why the previous steps are not feasible for your use case.


Build Succeeds But Doesn't Update
---------------------------------

**Symptoms:** You pushed new changes to your repository, but your documentation on Read the Docs isn't updating.

**Solutions:**

1.  **Wipe the Version**
    *   Go to your project's **Admin** tab on Read the Docs, navigate to the **Versions** page, and use the **“Wipe”** button for the version you are building. This clears the build environment and forces a complete rebuild.
2.  **Check Webhooks**
    *   If builds aren't triggering automatically at all, ensure your GitHub (or other VCS) webhook is configured correctly. See our guide on :doc:`webhooks <webhooks>`.

Build Succeeds But Documentation Looks Broken
---------------------------------------------

**Symptoms:** The build log shows no errors, but your site has missing CSS, broken layouts, or old content.

**Solutions:**

1.  **Rebuild Your Project**
    *   This is often caused by stale files on our servers. Trigger a manual rebuild of your project. This will force a sync of all web assets.
2.  **Hard Refresh Your Browser**
    *   Sometimes your browser caches old CSS/JS files. Do a hard refresh (``Ctrl + F5`` on Windows/Linux, ``Cmd + Shift + R`` on Mac) to clear the cache.

General Build Failure (Unknown Error)
-------------------------------------

**Symptoms:** The build fails with a generic error message that isn't covered in this guide.

**Solutions:**

1.  This often indicates a temporary problem on the Read the Docs side.
2.  First, try triggering a **rebuild**. If the problem persists, please `file a support ticket <https://readthedocs.org/support/>`_ and include your **Build ID** (you can find this in the build output log) so we can investigate.

Configuration File Errors
-------------------------

**Symptoms:** Build fails immediately with errors about your ``.readthedocs.yaml`` configuration.

**Solutions:**

1.  Most configuration errors are related to incorrect syntax or unsupported options.
2.  Please refer to our full :doc:`Configuration File V2 <config-file/v2>` documentation for the correct schema and examples.
3.  Common mistakes include incorrect indentation (use spaces, not tabs) and using a key that is not supported.

Getting More Help
-----------------

If you've tried the steps above and are still having issues, please contact us:

*   **For bugs with the Read the Docs service:** `File an issue on our GitHub tracker <https://github.com/readthedocs/readthedocs.org/issues>`_.
*   **For account and build problems:** `Submit a support request <https://readthedocs.org/support/>`_ and be sure to include your **build ID**.








