---
title: '&lt;entryPoint&gt; элемент (приложение ClickOnce) | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3002fa5c015d80304a9de5aaf3b7f7aa1d2d85f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629044"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;entryPoint&gt; элемент (приложение ClickOnce)
Идентифицирует сборку, которая должна быть выполнена, когда это [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение запускается на клиентском компьютере.

## <a name="syntax"></a>Синтаксис

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Элементы и атрибуты
 Элемент `entryPoint` является обязательным и находится в пространстве имен `urn:schemas-microsoft-com:asm.v2` . Может существовать только один `entryPoint` элементу, определенному в манифесте приложения.

 Элемент `entryPoint` имеет перечисленные ниже атрибуты.

|Атрибут|Описание|
|---------------|-----------------|
|`name`|Необязательный параметр. Это значение не используется платформой .NET Framework.|

 У элемента`entryPoint` имеются перечисленные ниже элементы.

## <a name="assemblyidentity"></a>assemblyIdentity
 Обязательный. Роль `assemblyIdentity` и его атрибуты, определенные в [ \<assemblyIdentity > элемент](../deployment/assemblyidentity-element-clickonce-application.md).

 `processorArchitecture` Атрибут этого элемента и `processorArchitecture` атрибутом, определенным в `assemblyIdentity` в другом месте в приложении манифест должен соответствовать.

## <a name="commandline"></a>commandLine
 Обязательный. Должен быть дочерним элементом `entryPoint` элемент. Он не имеет дочерних элементов и имеет следующие атрибуты.


| Атрибут | Описание |
|--------------| - |
| `file` | Обязательный. Локальную ссылку на сборку для запуска [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Это значение не может содержать косую черту (/) или обратную косую черту (\\) разделители путей. |
| `parameters` | Обязательный. Описывает действие, выполняемое с точкой входа. Единственным допустимым значением является `run`; Если передается пустая строка, `run` предполагается, что. |

## <a name="customhostrequired"></a>customHostRequired
 Необязательный параметр. Если включен, указывает, что это развертывание содержит компонент, который будет развернут в настраиваемом узле, а не является автономным приложением.

 Если этот элемент присутствует, `assemblyIdentity` и `commandLine` элементы не также должен присутствовать. Если Да, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] вызовут ошибки проверки во время установки.

 Этот элемент не имеет атрибутов и дочерних элементов.

## <a name="customux"></a>customUX
 Необязательный параметр. Указывает, что приложение устанавливается и обслуживается пользовательский установщик и не создает запись меню Пуск, клавиш или добавить и удалить запись программы.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Приложения, содержащего элемент customUX необходимо предоставить пользовательский установщик, использующий <xref:System.Deployment.Application.InPlaceHostingManager> классом для выполнения установки операций. Приложения с помощью этого элемента невозможно установить, дважды щелкнув его готовности к установке загрузчика setup.exe или манифеста. Можно создать пользовательский установщик, пункты меню Пуск, ярлыки и записи, Установка и удаление программ. Если пользовательский установщик не выполняет запись Установка и удаление программ, его необходимо сохранить идентификатор подписки, предоставляемый <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> свойство и включите пользователя для удаления приложения позже, вызвав <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> метод. Дополнительные сведения см. в разделе [Пошаговое руководство: Создание пользовательского установщика для приложения ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Примечания
 Этот элемент определяет, сборки и точки входа для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения.

 Нельзя использовать `commandLine` для передачи параметров в приложение во время выполнения. Можно открыть параметры строки запроса для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания из приложения <xref:System.AppDomain>. Дополнительные сведения см. в разделе [как: получить данные строки запроса в интерактивном приложении ClickOnce](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Пример
 В следующем примере кода показано `entryPoint` элемента в манифесте приложения для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. Данный пример кода является частью большего примера для [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md) раздела.

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>См. также
- [Манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md)
