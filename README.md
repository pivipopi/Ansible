# Ansible

- 플레이북을 이용하여 database와 wordpress를 생성하고 삭제한다.

# 생성

- 해당 레포지토리 clone
- Ansible/wp 디렉토리로 이동
- 변수, 호스트 파일 확인
```
cat ansible.cfg     # 인벤토리 지정
cat hosts.ini       # 호스트 그룹 확인

group_vars/port_var.yaml             # 공용 포트 변수
cat roles/database/vars/main.yaml    # 데이터 변수 확인
cat roles/wordpress/vars/main.yaml   # 웹상의 워드프레스 설정과 포트 설정 확인
```
- 실행
```
ansible-playbook site.yaml -b
```

# 삭제
- database와 wpordpress를 한 번에 삭제
```
ansible-playbook re-site.yaml -b
```

# 디렉토리 구조
```
.
├── ansible.cfg
├── group_vars
│       └── port_vars.yaml
├── hosts.ini
├── re-site.yaml
├── roles
│   ├── database
│   │   ├── handlers
│   │   │   └── main.yaml
│   │   ├── tasks
│   │   │   ├── debian.yaml
│   │   │   ├── main.yaml
│   │   │   └── redhat.yaml
│   │   └── vars
│   │       └── main.yaml
│   ├── re_database
│   │   └── tasks
│   │       └── main.yaml
│   ├── re_wordpress
│   │   └── tasks
│   │       └── main.yaml
│   └── wordpress
│       ├── handlers
│       │   └── main.yaml
│       ├── tasks
│       │   ├── debian.yaml
│       │   ├── main.yaml
│       │   └── redhat.yaml
│       ├── templates
│       │   ├── httpd.conf.j2
│       │   ├── ports.conf.j2
│       │   └── wp-config.php.j2
│       └── vars
│           └── main.yaml
└── site.yaml
```
