# alx-backend-python: Unittests and Integration Tests

## Description

This repository contains unit and integration tests for various utility functions and classes as part of the **ALX Backend Python** project. The focus is on writing parameterized tests, mocking HTTP calls, and understanding memoization.

## Tasks

### 0. Parameterize a Unit Test

**File:** `test_utils.py`

- Familiarize yourself with `utils.access_nested_map`.
- Implement a unit test in `TestAccessNestedMap` class.
- Use `@parameterized.expand` to test with multiple inputs.
- Ensure the method returns the expected results.

```python
from parameterized import parameterized
import unittest
from utils import access_nested_map

class TestAccessNestedMap(unittest.TestCase):
    @parameterized.expand([
        ({"a": 1}, ("a",), 1),
        ({"a": {"b": 2}}, ("a",), {"b": 2}),
        ({"a": {"b": 2}}, ("a", "b"), 2),
    ])
    def test_access_nested_map(self, nested_map, path, expected):
        self.assertEqual(access_nested_map(nested_map, path), expected)

    @parameterized.expand([
        ({}, ("a",)),
        ({"a": 1}, ("a", "b")),
    ])
    def test_access_nested_map_exception(self, nested_map, path):
        with self.assertRaises(KeyError):
            access_nested_map(nested_map, path)
```

### 1. Mock HTTP Calls

**File:** `test_utils.py`

- Familiarize yourself with `utils.get_json`.
- Implement a unit test in `TestGetJson` class.
- Use `unittest.mock.patch` to mock `requests.get`.

```python
from unittest.mock import patch, Mock
from utils import get_json

class TestGetJson(unittest.TestCase):
    @parameterized.expand([
        ("http://example.com", {"payload": True}),
        ("http://holberton.io", {"payload": False}),
    ])
    def test_get_json(self, test_url, test_payload):
        with patch('requests.get') as mock_get:
            mock_get.return_value = Mock(**{"json.return_value": test_payload})
            self.assertEqual(get_json(test_url), test_payload)
            mock_get.assert_called_once_with(test_url)
```

### 2. Parameterize and Patch

**File:** `test_utils.py`

- Familiarize yourself with `utils.memoize`.
- Implement a unit test in `TestMemoize` class.

```python
from unittest.mock import patch
from utils import memoize

class TestMemoize(unittest.TestCase):
    def test_memoize(self):
        class TestClass:
            def a_method(self):
                return 42

            @memoize
            def a_property(self):
                return self.a_method()

        with patch.object(TestClass, 'a_method', return_value=42) as mock_method:
            test_instance = TestClass()
            self.assertEqual(test_instance.a_property, 42)
            self.assertEqual(test_instance.a_property, 42)
            mock_method.assert_called_once()
```

### 3. Parameterize and Patch as Decorators

**File:** `test_client.py`

- Familiarize yourself with `client.GithubOrgClient`.
- Implement a unit test in `TestGithubOrgClient` class.

```python
from unittest.mock import patch
from client import GithubOrgClient

class TestGithubOrgClient(unittest.TestCase):
    @parameterized.expand([
        ("google",),
        ("abc",),
    ])
    @patch('client.get_json', return_value={"payload": True})
    def test_org(self, org_name, mock_get_json):
        client = GithubOrgClient(org_name)
        self.assertEqual(client.org, {"payload": True})
        mock_get_json.assert_called_once_with(f'https://api.github.com/orgs/{org_name}')
```

### 4. Mocking a Property

**File:** `test_client.py`

- Implement the `test_public_repos_url` method.

```python
from unittest.mock import patch, PropertyMock
from client import GithubOrgClient

class TestGithubOrgClient(unittest.TestCase):
    @patch('client.GithubOrgClient.org', new_callable=PropertyMock)
    def test_public_repos_url(self, mock_org):
        mock_org.return_value = {"repos_url": "http://some_url"}
        client = GithubOrgClient("org_name")
        self.assertEqual(client._public_repos_url, "http://some_url")
```

### 5. More Patching

**File:** `test_client.py`

- Implement the `test_public_repos` method.

```python
from unittest.mock import patch
from client import GithubOrgClient

class TestGithubOrgClient(unittest.TestCase):
    @patch('client.get_json', return_value=[{"name": "repo1"}, {"name": "repo2"}])
    @patch('client.GithubOrgClient._public_repos_url', new_callable=PropertyMock)
    def test_public_repos(self, mock_public_repos_url, mock_get_json):
        mock_public_repos_url.return_value = "http://some_url"
        client = GithubOrgClient("org_name")
        self.assertEqual(client.public_repos(), ["repo1", "repo2"])
        mock_get_json.assert_called_once_with("http://some_url")
```

### 6. Parameterize

**File:** `test_client.py`

- Implement the `test_has_license` method.

```python
from parameterized import parameterized
from client import GithubOrgClient

class TestGithubOrgClient(unittest.TestCase):
    @parameterized.expand([
        ({"license": {"key": "my_license"}}, "my_license", True),
        ({"license": {"key": "other_license"}}, "my_license", False),
    ])
    def test_has_license(self, repo, license_key, expected):
        client = GithubOrgClient("org_name")
        self.assertEqual(client.has_license(repo, license_key), expected)
```

### 7. Integration Test: Fixtures

**File:** `test_client.py`

- Implement `TestIntegrationGithubOrgClient` class.

```python
from parameterized import parameterized_class
from unittest.mock import patch
from client import GithubOrgClient

@parameterized_class([
    {"org_payload": {...}, "repos_payload": [...], "expected_repos": [...], "apache2_repos": [...]},
])
class TestIntegrationGithubOrgClient(unittest.TestCase):
    @classmethod
    def setUpClass(cls):
        cls.get_patcher = patch('requests.get')
        cls.mock_get = cls.get_patcher.start()
        cls.mock_get.side_effect = lambda url: Mock(json=lambda: {...})

    @classmethod
    def tearDownClass(cls):
        cls.get_patcher.stop()

    def test_public_repos(self):
        client = GithubOrgClient("org_name")
        self.assertEqual(client.public_repos(), self.expected_repos)

    def test_public_repos_with_license(self):
        client = GithubOrgClient("org_name")
        self.assertEqual(client.public_repos(license="apache-2.0"), self.apache2_repos)
```

## Repository Structure

```
alx-backend-python/
│
├── 0x03-Unittests_and_integration_tests/
│   ├── test_utils.py
│   └── test_client.py
└── README.md
```

## Usage

1. Clone the repository:

```bash
git clone https://github.com/your_username/alx-backend-python.git
```

2. Navigate to the project directory:

```bash
cd alx-backend-python/0x03-Unittests_and_integration_tests
```

3. Run the tests:

```bash
python -m unittest discover
```

## Author

- Ian Wainaina Kamau - [GitHub](https://github.com/Nainah23)
