---
title: Развертывание расширения модели слоев | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 63538797f335cab770f3748d946b08de6b44c609
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58994170"
---
# <a name="deploy-a-layer-model-extension"></a>Развертывание расширения модели слоев
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Другие пользователи Visual Studio могут устанавливать расширения моделирования слоев, созданные вами с помощью Visual Studio.  
  
## <a name="installing-your-extension"></a>Установка расширения  
 Расширение скомпилировано в VSIX-файл, который можно устанавливать на других компьютерах. Кроме того, расширение можно установить на компьютере разработки, чтобы сделать его доступным в главном экземпляре Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Установка расширения  
  
1. В проекте, который содержит **source.vsix.manifest**откройте **bin\\\\*** в проводнике.  
  
2. Копировать  **\*.vsix** файл на компьютер, на котором требуется установить расширение.  
  
3. На конечном компьютере дважды щелкните VSIX-файл в проводнике.  
  
    Откроется установщик VSIX.  
  
#### <a name="to-uninstall-the-extension"></a>Удаление расширения  
  
1.  В Visual Studio на **средства** меню, щелкните **расширения и обновления**.  
  
2.  Щелкните имя расширения и нажмите кнопку **удаления**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Установка расширения на сервере Team Foundation Build  
 Как правило, на серверах [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] не установлена среда Visual Studio, поэтому установить VSIX двойным щелчком мыши невозможно. Установка [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] включает несколько компонентов для запуска расширения VSIX, но установка расширения выполняется вручную.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildincludesesprbuild-mdmd-server"></a>Установка расширения слоев на сервере [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]  
  
1.  Копировать **.vsix** файлы с компьютера разработки на [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] компьютера.  
  
     Поместите VSIX-файл в одно из указанных ниже мест.  
  
    -   Установка для всех пользователей и служб:  
  
         %ProgramFiles%\Microsoft Visual Studio [версия]\Common7\IDE\Extensions\Microsoft  
  
    -   Установка только для сетевой службы, в которой выполняется [!INCLUDE[esprbuild](../includes/esprbuild-md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
    -   Если сервер [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] настроен на выполнение в интерактивном режиме от имени определенного пользователя, установить расширение можно только для этого пользователя:  
  
         %LocalAppData%\Microsoft\VisualStudio\\[version]\Extensions\Microsoft  
  
        > [!NOTE]
        >  % LocalAppData % — *DriveName*: пользователи*UserName*AppDataLocal.  
  
2.  Разверните каждый VSIX-файл в папке в том же местоположении.  
  
    1.  Измените расширение имени файла с **.vsix** для **ZIP-файл**.  
  
    2.  Извлеките содержимое ZIP-файла в папку.  
  
    3.  Удалите ZIP-файл.  
  
3.  Перезапустите [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].
