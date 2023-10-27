# Sony Headphones Bluetooth Documentation

This page is a collection of information about the Sony Headphones Bluetooth protocol. It is a work in progress and gets updated as we find out more about the protocol. If you have any information that you would like to add, please feel free to submit a pull request.

The documentation is not affiliated with or endorsed by Sony Corporation or any of its subsidiaries in any way.

## Contribute

If you would like to contribute to this documentation, please feel free to submit a pull request. Please make sure
that your modified documentation builds and runs correctly before submitting a pull request.

### Building

To install this documentation, you will require Python >= 3.9 and pip. Find the install instructions for Python on the internet.
You can install pip by running the `ensurepip` module with Python.

```bash
python -m ensurepip --upgrade
```

You should install the dependencies in a virtual environment. To create a virtual environment, run the following command.

```bash
python -m venv venv
```

To activate the virtual environment, run the following command.

- Linux/macOS:
    
    ```bash
    source venv/bin/activate
    ```

- Windows:

    ```bash
    venv\Scripts\activate.bat
    ```

To install the dependencies, run the following command.

```bash
pip install -r requirements.txt
```

To build and serve the documentation on localhost, run the following command.

```bash
mkdocs serve
```

# Website

The website for this documentation can be found [here](https://ohm-app.github.io/sony-headphones-bluetooth-documentation/).

## License

This documentation falls under the public domain via the [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/) license.