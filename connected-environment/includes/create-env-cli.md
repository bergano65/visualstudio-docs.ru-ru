## <a name="create-a-kubernetes-development-environment-in-azure"></a>Создание среды разработки Kubernetes в Azure
С помощью подключенных сред можно создавать среды на основе Kubernetes, полностью управляемые Azure и оптимизированные для разработки. Эта команда создает среду с именем `mydevenvironment` в `eastus`.
```cmd
vsce env create --name mydevenvironment --location eastus
```

Поддерживаемые расположения: `eastus`, `westeurope`

> [!Note]
> Выполнение этой команды занимает около шести минут. А пока вы можете продолжить изучение руководства.
