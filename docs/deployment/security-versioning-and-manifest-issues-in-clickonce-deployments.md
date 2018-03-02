---
title: "Управление версиями, проблем безопасности и манифестов в развертываниях ClickOnce | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- versioning, ClickOnce applications
- ClickOnce applications, Windows Vista User Account Control
- ClickOnce applications, versioning issues
- security, ClickOnce applications
- Windows 7, ClickOnce deployments
- ClickOnce applications, manifest issues
- User Account Control, ClickOnce applications
- Windows Vista, ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, security issues
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 2dd693a35725d41b2b8ced99d78bd4a62d8d9e3a
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Вопросы безопасности, контроля версий и манифестов в развертываниях ClickOnce

Существует множество проблем с [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] безопасности, управление версиями приложений и манифеста синтаксис и семантику, которая может вызвать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] неудачного развертывания.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce и контроля учетных записей Windows Vista

В [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], приложения по умолчанию выполняются в режиме обычного пользователя, даже если текущий пользователь вошел с учетной записью, имеющей права администратора. Если приложение должно выполнить действие, требующее разрешений администратора, он показывает, в операционную систему, которая затем предлагает пользователю ввести учетные данные администратора. Эта функция, называемая управления учетных записей (UAC), предотвращает внесение изменений, которые могут повлиять на всю операционную систему без явного подтверждения пользователя приложениями. Приложения Windows объявляют, что ему требуется данное повышение уровня разрешений, указав `requestedExecutionLevel` атрибута в `trustInfo` разделе своего манифеста приложения.

Из-за риска сделать приложения уязвимыми к атакам [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений не могут запрашивать повышение уровня разрешений, если включен контроль учетных Записей для клиента. Любой [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения, которое пытается установить его `requestedExecutionLevel` атрибут `requireAdministrator` или `highestAvailable` не будут устанавливаться на [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].

В некоторых случаях вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет выполнена попытка запустить с правами администратора из-за алгоритма обнаружения установщика [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. В этом случае можно задать `requestedExecutionLevel` атрибута в манифесте приложения для `asInvoker`. Это вызовет само приложение, чтобы запустить без повышения уровня разрешений. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] 

Если вы разрабатываете приложение, необходимы права администратора в течение всего времени существования приложения, следует рассмотреть возможность развертывания приложения с помощью технологии установщика Windows (MSI), вместо этого. Дополнительные сведения см. в разделе [основы установщика Windows](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Квоты интерактивных приложений и частичного доверия приложения

Если ваш [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение выполняется в интерактивном режиме, а не через установку, оно должно попадать в квоту, установленную для интерактивных приложений. Кроме того сетевое приложение, выполняющееся с частичным доверием, например с ограниченным набором разрешений безопасности не может быть больше половины размера квоты.

Дополнительные сведения и инструкции о способах изменения квоты интерактивных приложений см. в разделе [Общие сведения о кэше ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Проблемы с управлением версиями

Если назначить строгое имя сборки и увеличить номер версии сборки для отражения обновления приложения, могут возникнуть проблемы. Какой-либо сборки, скомпилированные со ссылкой на сборку строгим именем должна быть сама перекомпилирована, или сборка будет пытаться ссылаться на более раннюю версию. Сборка попробуйте это, поскольку эта сборка использует старое значение версии в запросе привязки.

Например предположим, что сборки со строгим именем в своем собственном проекте с версией 1.0.0.0. После компиляции сборки, можно добавить как ссылку на проект, содержащий главное приложение. Если обновить сборку, увеличить версию до 1.0.0.1 и попытаться развернуть ее без перекомпиляции приложения, приложение будет невозможно загрузить сборку во время выполнения.

Эта ошибка может возникать только в том случае, если вы изменяете вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесты вручную; Эта ошибка не должна возникать при создании развертывания с помощью Visual Studio.

## <a name="specifying-individual-net-framework-assemblies-in-the-manifest"></a>Указание в манифесте сборки отдельных .NET Framework

Приложение не будет работать, если необходимо вручную внести изменения в загрузке [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания для ссылки на более старую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] сборки. Например, если вы добавили ссылку на сборку System.Net для версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] до версии, указанной в манифесте, затем возникнет ошибка. В общем случае не следует указывать ссылки на отдельные [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] сборки, как версия [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] от которой работает приложение задается как зависимость в манифесте приложения.

## <a name="manifest-parsing-issues"></a>Проблемы синтаксического анализа манифеста

Файлы манифеста, которые используются в [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] являются XML-файлы, и они должны быть корректным и допустимым: они должны подчиняться правилам синтаксиса XML, используйте только элементы и атрибуты, определенные в соответствующей схеме XML.

То, что может вызвать проблемы в файле манифеста выбирает имя для приложения, которое содержит специальные символы, такие как одинарные или двойные кавычки. Имя приложения является частью его [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] удостоверений. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]  Если приложение не удается активировать, убедитесь, что для имени используются только буквенные и цифровые символы и попытаться повторить развертывание.

Если манифесты развертывания или приложения было изменено вручную, то может их непреднамеренное повреждение. Поврежденный манифест будет препятствовать правильной [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установки. Можно устранить такие ошибки во время выполнения, нажав кнопку **сведения** на **ошибка ClickOnce** диалоговое окно и чтения сообщение об ошибке в журнале. В журнале будет содержаться одно из следующих сообщений:

- Синтаксическая ошибка, номер строки и знак Описание позиции, где произошла ошибка.

- Имя элемента или атрибута, используемого в нарушение схемы манифеста. Если вы добавили XML вручную в манифест, необходимо сравнить добавления со схемами манифеста. Дополнительные сведения см. в разделе [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) и [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).

- Конфликт Идентификаторов. Ссылки на зависимости в манифестах развертывания и приложений должно быть уникальным в обоих их `name` и `publicKeyToken` атрибуты. Если оба атрибута совпадают для любых двух элементов в манифесте, синтаксический анализ манифеста не будет выполнено.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Меры предосторожности при изменении манифестов или приложений вручную

При обновлении манифеста приложения, необходимо повторно подписать манифест приложения и манифест развертывания. Манифест развертывания содержит ссылку на манифест приложения, содержащий хэш этого файла и его цифровой подписи.

### <a name="precautions-with-deployment-provider-usage"></a>Меры предосторожности при использовании поставщика развертываний

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Манифест развертывания имеет `deploymentProvider` свойство, которое указывает полный путь к расположению, из которой приложение необходимо устанавливать и обслуживание:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Этот путь задается [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] создает приложение и является обязательным для установленных приложений. Путь указывает на стандартное расположение где [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установщика для установки приложения и поиск обновлений. Если вы используете **xcopy** команду, чтобы скопировать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в другое расположение, но не изменяют `deploymentProvider` свойство, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет по-прежнему ссылаться в исходное расположение при попытке загрузить приложение.

Если требуется переместить или скопировать приложение, необходимо также обновить `deploymentProvider` пути, чтобы фактически установки клиента в новом расположении. Обновление этого пути является главным образом при установке приложения. Для интерактивных приложений, которые всегда запускаются через исходный URL-адрес, параметр `deploymentProvider` является необязательным. Если `deploymentProvider` не установлен, он будет учитываться; в противном случае URL-адрес, используемый для запуска приложения будет использоваться как базовый URL-адрес для загрузки файлов приложения.

> [!NOTE]
> При каждом обновлении манифеста необходимо также подписать его еще раз.

## <a name="see-also"></a>См. также

[Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)  
[Защита приложений ClickOnce](../deployment/securing-clickonce-applications.md)  
[Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)