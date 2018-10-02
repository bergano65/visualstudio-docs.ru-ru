---
title: Развертывание расширения модели слоев | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layer diagrams, deploying extensions
- layer models, deploying extensions
ms.assetid: 00a4675b-d20e-487e-8fd5-be2b1e0ba238
caps.latest.revision: 29
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: b5d581ca67a2d3fde5b7acab5937d1aedf88cfa4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559893"
---
# <a name="deploy-a-layer-model-extension"></a>Развертывание расширения модели слоев
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [развертывание расширения модели слоев](https://docs.microsoft.com/visualstudio/modeling/deploy-a-layer-model-extension).  
  
Другие пользователи Visual Studio могут устанавливать расширения моделирования слоев, созданные вами с помощью Visual Studio.  
  
## <a name="installing-your-extension"></a>Установка расширения  
 Расширение скомпилировано в VSIX-файл, который можно устанавливать на других компьютерах. Кроме того, расширение можно установить на компьютере разработки, чтобы сделать его доступным в главном экземпляре Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Установка расширения  
  
1.  В проекте, который содержит **source.vsix.manifest**откройте **bin\\ \***  в проводнике.  
  
2.  Копировать  **\*.vsix** файл на компьютер, на котором требуется установить расширение.  
  
3.  На конечном компьютере дважды щелкните VSIX-файл в проводнике.  
  
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



