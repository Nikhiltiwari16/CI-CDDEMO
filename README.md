# CI-CDDEMO
This is an demo for CI/CD pipeline
This is an Beginning of the CI/CD
import pytest
from app import app


@pytest.fixture
def client():
    app.config['TESTING'] = True
    with app.test_client() as client:
        yield client


def test_app_is_working(client):
    response = client.get('/')
    assert response.status_code == 200
    assert b"Hello World!" in response.data
