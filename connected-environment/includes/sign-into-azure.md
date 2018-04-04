## <a name="sign-in-to-azure"></a>Вход в Azure
Нам нужно будет войти в Azure, чтобы создать нашу среду разработки. В окне терминала введите следующую команду:
```cmd
az login
```

> [!Note]
> Если у вас нет подписки Azure, вы можете создать [бесплатную учетную запись](https://azure.microsoft.com/free).

### <a name="if-you-have-multiple-azure-subscriptions"></a>Если у вас несколько подписок Azure...
Вы можете просмотреть подписки, выполнив: 
```cmd
az account list
```
Найдите подписку, имеющую `isDefault: true` в выходных данных JSON.
Если вы хотите использовать не эту подписку, можно изменить подписку по умолчанию:
```cmd
az account set --subscription <subscription ID>
```
