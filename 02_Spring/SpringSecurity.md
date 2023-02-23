# SpringSecurity

## ユーザを読み込む(UserDetailsServiceインターフェース)

### やりたいこと

1. 認証に必要なユーザ情報をDBから読み込む
2. User形で返却をする

### やり方

- クラスの定義　UserDetailsServiceを継承する

```java
@Service
public class UserDetailsServiceImpl implements UserDetailsService {
```

- メソッドの再定義　loadUserByUsernameを再定義

  - Ｕser型で返却

  ``` java
  		Set<GrantedAuthority> graAuthorities = new HashSet<>();
  		graAuthorities.add(new SimpleGrantedAuthority("ROLE_USER"));
  		
  		return new User(user.getUsername(), user.getPassword(), graAuthorities);
  ```

  

