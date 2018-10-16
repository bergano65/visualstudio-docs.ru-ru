---
title: Управление версиями, вопросы безопасности и манифестов в развертываниях ClickOnce | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a7ae835b53960ca6952b71c10a2348f707785e16
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/17/2018
ms.locfileid: "39081749"
---
# <a name="security-versioning-and-manifest-issues-in-clickonce-deployments"></a>Управление версиями, вопросы безопасности и манифестов в развертываниях ClickOnce

Существует множество проблем, возникающих при [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] безопасности, управление версиями приложений и манифеста синтаксиса и семантики, которые могут вызвать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] неудачного развертывания.

## <a name="clickonce-and-windows-vista-user-account-control"></a>ClickOnce и контроль учетных записей пользователей Windows Vista

В [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)], приложений по умолчанию запуск от имени обычного пользователя, даже если текущий пользователь вошел с учетной записью, имеющей права администратора. Если приложение должно выполнить действие, требующее разрешений администратора, он сообщает операционной системы, которая затем предлагает пользователю ввести свои учетные данные администратора. Эта функция, которая называется контроля учетных записей (UAC), запрещает приложениям вносить изменения, которые могут повлиять на всю операционную систему без явного согласия пользователя. Приложения Windows объявляют, что они требуют это повышение уровня разрешений, указав `requestedExecutionLevel` атрибут в `trustInfo` разделе своего манифеста приложения.

Из-за риска сделать приложения уязвимыми к атакам [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложений не могут запрашивать повышение уровня разрешений, если UAC включен для клиента. Любой [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение, которое пытается установить его `requestedExecutionLevel` атрибут `requireAdministrator` или `highestAvailable` не установится на [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)].

В некоторых случаях ваши [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение может попытаться запуск с правами администратора, из-за алгоритма обнаружения установщика в [!INCLUDE[windowsver](../deployment/includes/windowsver_md.md)]. В этом случае можно задать `requestedExecutionLevel` атрибут в манифесте приложения для `asInvoker`. В результате само приложение, чтобы запустить без повышения прав. [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Этот атрибут автоматически добавляет все манифесты приложений.

Если вы разрабатываете приложение, для которой требуются права администратора в течение всего времени существования приложения, следует рассмотреть возможность развертывания приложения с помощью технологии установщика Windows (MSI), вместо этого. Дополнительные сведения см. в разделе [основные сведения об установщике Windows](../extensibility/internals/windows-installer-basics.md).

## <a name="online-application-quotas-and-partial-trust-applications"></a>Квоты интерактивных приложений и приложений с частичным доверием

Если ваш [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение выполняется в интерактивном режиме, а не через установку, оно должно попадать в квоту, установленную для интерактивных приложений. Кроме того сетевое приложение, которое работает в режиме частичного доверия, например, с ограниченным набором разрешений безопасности, не может быть больше половины размера квоты.

Дополнительные сведения и инструкции о способах изменения квоты интерактивных приложений, см. в разделе [Общие сведения о кэше ClickOnce](../deployment/clickonce-cache-overview.md).

## <a name="versioning-issues"></a>Проблемы с управлением версиями

Если назначить строгое имя сборки и увеличить номер версии сборки для отражения обновления приложения, могут возникнуть проблемы. Любой сборки, скомпилированные со ссылкой на сборку со строгим именем сам перекомпилируется, или сборка будет пытаться ссылаться на более старой версии. Сборки попробуйте это, так как сборка использует старое значение версии в запросе привязки.

Например предположим, что является сборкой со строгим именем в своем собственном проекте с помощью версии 1.0.0.0. После компиляции сборки, добавьте его как ссылку на проект, содержащий главное приложение. Если обновить сборку, увеличить версию на 1.0.0.1 и попытаться развернуть ее без перекомпиляции приложения, приложение будет невозможно загрузить сборку во время выполнения.

Эта ошибка может возникать только в том случае, если вы редактируете вашей [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] манифесты вручную и не должны появляться Данная ошибка, при создании развертывания с помощью Visual Studio.

## <a name="specify-individual-net-framework-assemblies-in-the-manifest"></a>Укажите отдельных сборок платформы .NET Framework в манифесте

Приложение не будет работать для загрузки, если изменено вручную [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания для ссылки на более старую версию [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] сборки. Например, если вы добавили ссылку на сборку System.Net для версии [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] до версии, указанной в манифесте, то может возникнуть ошибка. В общем случае не следует указывать ссылки на отдельные [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] сборки, как версия [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] от которой работает приложение указано как зависимость в манифесте приложения.

## <a name="manifest-parsing-issues"></a>Манифест, ошибок при анализе

Файлы манифеста, используемые [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] являются файлами XML, и они должны быть правильным форматом и допустимым: они должны подчиняются правилам синтаксиса XML и использовать только элементы и атрибуты, определенные в соответствующей схемы XML.

То, что может вызвать проблемы в файл манифеста является выбор имя приложения, которое содержит специальный символ, например использовать одинарные или двойные кавычки. Имя приложения является частью его [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] удостоверений. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] в настоящее время не выполняет анализ удостоверений, которые содержат специальные символы. Если не удается активировать приложение, убедитесь, что вы используете только буквенные и цифровые символы для имени и пытаться развернуть его снова.

Вручную после редактирования вашего развертывания или манифест приложения, вы может непреднамеренно повредить их. Поврежденный манифест будет препятствовать правильной [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установки. Можно устранить такие ошибки во время выполнения, щелкнув **сведения** на **ошибка ClickOnce** диалоговое окно и чтении сообщение об ошибке в журнале. В журнале будет содержаться одно из следующих сообщений:

- Описание синтаксическая ошибка и номер строки и позицию, где произошла ошибка.

- Имя элемента или атрибута, используемого в нарушение схемы манифеста. Если вы добавили XML вручную в манифест, необходимо сравнить добавления со схемами манифеста. Дополнительные сведения см. в разделе [манифест развертывания ClickOnce](../deployment/clickonce-deployment-manifest.md) и [манифест приложения ClickOnce](../deployment/clickonce-application-manifest.md).

- Конфликт Идентификаторов. Ссылки на зависимости в манифестах развертывания и приложения должно быть уникальным в обоих их `name` и `publicKeyToken` атрибуты. Если оба атрибута совпадают для любых двух элементов в манифесте, синтаксический анализ манифеста не будет выполнено.

## <a name="precautions-when-manually-changing-manifests-or-applications"></a>Меры предосторожности при изменении манифеста или приложений вручную

Когда вы обновляете манифест приложения, необходимо повторно подписать манифест приложения и манифест развертывания. Манифест развертывания содержит ссылку на манифест приложения, которая включает хэш этого файла и его цифровой подписи.

### <a name="precautions-with-deployment-provider-usage"></a>Меры предосторожности при использовании поставщика развертываний

[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Манифест развертывания содержит `deploymentProvider` свойство, которое указывает полный путь к папке, из которой должны быть установлены и обслуживание приложения:

```xml
<deploymentProvider codebase="http://myserver/myapp.application" />
```

Этот путь задается, если [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] создает приложение и является обязательным для установленных приложений. Путь указывает на стандартное расположение где [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] установщик установит приложение и поиск обновлений. При использовании **xcopy** команду, чтобы скопировать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения в другое расположение, но не изменяйте `deploymentProvider` свойство, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] будет по-прежнему ссылаться в исходное расположение при попытке загрузить приложение.

Если вы хотите переместить или скопировать приложение, необходимо также обновить `deploymentProvider` пути, таким образом, чтобы клиент фактически устанавливается из нового расположения. Обновление этого пути является главным образом после установки приложения. Для интерактивных приложений, которые всегда запускаются через исходный URL-адрес, параметр `deploymentProvider` является необязательным. Если `deploymentProvider` не установлен, он будет учитываться; в противном случае — значение URL-адрес, используемый для запуска приложения будет использоваться как базовый URL-адрес для загрузки файлов приложения.

> [!NOTE]
> Каждый раз при обновлении манифеста необходимо также подписать его снова.

## <a name="see-also"></a>См. также

[Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)  
[Securw ClickOnce-приложений](../deployment/securing-clickonce-applications.md)  
[Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)