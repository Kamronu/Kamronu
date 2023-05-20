import requests
import json

def create_github_repo(repo_name, access_token):
    headers = {
        'Authorization': f'token {access_token}',
        'Accept': 'application/vnd.github.v3+json'
    }

    data = {
        'name': repo_name,
        'description': 'My GitHub repository',
        'private': False,  # Установите True, чтобы создать приватный репозиторий
        'auto_init': True  # Установите False, если вы не хотите инициализировать репозиторий с файлом README.md
    }

    response = requests.post('https://api.github.com/user/repos', headers=headers, data=json.dumps(data))

    if response.status_code == 201:
        print(f"Репозиторий '{repo_name}' успешно создан!")
    else:
        print("Не удалось создать репозиторий. Проверьте правильность токена доступа.")

# Замените YOUR_ACCESS_TOKEN на ваш личный токен доступа
access_token = 'YOUR_ACCESS_TOKEN'
repo_name = 'my-repo'

create_github_repo(repo_name, access_token)
