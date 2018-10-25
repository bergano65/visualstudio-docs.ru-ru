---
title: Предварительные условия для развертывания приложения | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 421092218cdeb889fe195917e46b123c73e7e1f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851807"
---
# <a name="application-deployment-prerequisites"></a>Предварительные условия для развертывания приложения

Чтобы приложение для установки и запуска успешно, необходимо сначала установите все компоненты, от которых зависит приложение на целевом компьютере. Например, большинство приложений, созданных с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] зависят от [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. В этом случае правильную версию среда CLR должен присутствовать на конечном компьютере перед установкой приложения.  

 Можно выбрать эти компоненты в **Prerequisites Dialog Box** и установить .NET Framework и любые другие распространяемые в ходе установки. Такой подход известен как *начальная загрузка*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создает исполняемую программу Windows с именем *Setup.exe*, также известных как *загрузчика*. Начальный загрузчик установит необходимые компоненты перед запуском приложения. Дополнительные сведения о выборе необходимых компонентов, см. в разделе [одноименном диалоговом окне](../ide/reference/prerequisites-dialog-box.md).  

 Каждый необходимый компонент является пакетом начальной загрузки. Пакет начального загрузчика — это группа каталогов и файлов, содержащих файлы манифеста, которые описывают, как устанавливаются необходимые компоненты. Если необходимых для вашего приложения не указаны в **диалоговое окно готовности к установке**, можно создать настраиваемые пакеты загрузчика и добавить их в Visual Studio. Затем можно выбрать необходимые компоненты в **Prerequisites Dialog Box**. Дополнительные сведения см. в разделе [создание пакетов начального загрузчика](../deployment/creating-bootstrapper-packages.md).  

 По умолчанию для развертывания приложений ClickOnce начальная загрузка включена, а генерируемый для них начальный загрузчик подписан. Вы можете отключить начальную загрузку компонента, но только в том случае, если вы уверены, что на всех целевых компьютерах уже установлена правильная версия компонента.  

## <a name="bootstrapping-and-clickonce-deployment"></a>Начальная загрузка и ClickOnce развертывания  
 Перед установкой приложения на клиентском компьютере, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] проверяет клиента, чтобы гарантировать, что он имеет требованиям, указанным в манифесте приложения. К ним относятся следующие требования:  

- Минимальная необходимая версия среды CLR, определенная в качестве зависимости от сборки в манифесте приложения.  

- Минимальная версия операционной системы Windows, необходимая для приложения, согласно манифесту приложения с использованием элемента `<osVersionInfo>`. (См. в разделе [ \<зависимостей > элемент](../deployment/dependency-element-clickonce-application.md).)  

- Минимальная версия все сборки, которые должны быть предварительно установлены в глобальный кэш сборок (GAC), как указано в декларации зависимости от сборки в манифесте сборки.  

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] можно определить недостающие необходимые компоненты и необходимые компоненты можно установить с помощью загрузчика. Дополнительные сведения см. в разделе [как: Установка необходимых компонентов для приложения ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  

> [!NOTE]
>  Чтобы изменить значения в манифестах, создаваемое набором средств, таких как [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и *MageUI.exe*, необходимо изменить манифест приложения в текстовом редакторе, а затем заново подписать манифесты приложения и развертывания. Дополнительные сведения см. в разделе [как: повторное подписание манифестов приложения и развертывания](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  

 Если для развертывания приложения используются Visual Studio и ClickOnce, то выбираемые по умолчанию пакеты начального загрузчика будут зависеть от версии .NET Framework в решении. Тем не менее, если изменить целевую версию .NET Framework, необходимо обновить параметры в **Prerequisites Dialog Box** вручную.  

|Целевая версия .NET Framework|Выбранные пакеты начального загрузчика|  
|---------------------------|------------------------------------|  
|Клиентский профиль .NET Framework 4|Клиентский профиль .NET Framework 4<br /><br /> Установщик Windows версии 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Установщик Windows версии 3.1|  

 С помощью [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания, *Publish.htm* страница [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] указывается мастера публикации, либо ссылку, которая устанавливает только приложение, или к связи, на которых установлены приложения и начальной загрузки компоненты.  

 Если начальный загрузчик генерируется с помощью мастера публикации ClickOnce или страницы публикации в Visual Studio *Setup.exe* подписывается автоматически. Если же для подписи начального загрузчика необходимо использовать сертификат клиента, то файл можно подписать позже.  

## <a name="bootstrapping-and-msbuild"></a>Начальная загрузка и MSBuild  
 Если вы не используете [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], но вместо компилируете приложения в командной строке, вы можете создать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложение начальной загрузки с помощью задачи Microsoft Build Engine (MSBuild). Дополнительные сведения см. в разделе [задача GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).  

 В качестве альтернативы начальному загрузчику можно предварительно развернуть компоненты с помощью электронной системы распределения, например Microsoft Systems Management Server (SMS).  

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Аргументы командной строки начального загрузчика (Setup.exe)  
 *Setup.exe* созданные [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и задач MSBuild, поддерживает следующий набор аргументов командной строки. Все остальные аргументы передаются установщика приложения.  

 Если изменить любые параметры начального загрузчика, необходимо изменить неподписанный начальный загрузчик, а затем подписать файл начального загрузчика.  


| Аргумент командной строки | Описание |
| - | - |
| **-?, -h, - справки** | Открывает диалоговое окно "Справка". |
| **-URL-адрес, - componentsurl** | Показывает сохраненный URL и URL-адреса компонентов для этой установки. |
| **-URL-адрес =** `location` | Задает URL-адрес которой *Setup.exe* будет искать [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] приложения. |
| **-componentsurl =** `location` | Задает URL-адрес которой *Setup.exe* будет искать зависимости, такие как [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. |
| **-homesite =** `true`**&#124;** `false` | Когда `true`, то зависимости загружаются из предпочтительного источника на сайте поставщика. Этот параметр переопределяет **- componentsurl** параметр. Когда `false`, то зависимости загружаются по URL-адрес, определяемое **- componentsurl**. |

## <a name="operating-system-support"></a>Поддержка операционной системой  
 Начальный загрузчик Visual Studio не поддерживается на основных серверных компонентов Windows Server 2008 или Windows Server 2008 R2 Server Core, поскольку они предоставляют незначительную поддержку серверной среды с ограниченной функциональностью. Например вариант установки Server Core поддерживает только профиль .NET Framework 3.5 Server Core, который не удается запустить средства Visual Studio, которые зависят от полной версии платформы .NET Framework.  

## <a name="see-also"></a>См. также  
 [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Развертывание и безопасность технологии ClickOnce](../deployment/clickonce-security-and-deployment.md)