---
title: "Переопределение диспетчера содержимого справки | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-help-viewer
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: c4889d40e9ca53cccf7de384e609eb959d8981f5
ms.contentlocale: ru-ru
ms.lasthandoff: 05/13/2017

---
# <a name="help-content-manager-overrides"></a>Переопределение диспетчера содержимого справки
Можно внести изменения в реестр для изменения поведения по умолчанию средства просмотра справки и связанных со справкой возможностей в интегрированной среде разработки Visual Studio.  
  
|Задача|Раздел реестра .|Значение и определение|  
|----------|------------------|--------------------------|  
|Указание уникальной конечной точки службы|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|  
|Укажите значение по умолчанию "в сети" или "вне сети"|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp — введите `0` для указания локальной справки или введите `1` для указания справки в Интернете.|  
|Указание уникальной конечной точки F1|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|  
|Переопределение приоритета задания BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (на 64-разрядном компьютере)\Microsoft\Help\v2.2|BITSPriority — используйте одно из следующих значений: **foreground**, **high**, **normal** или **low**.|  
|Отключение режима "в сети" (и параметра интегрированной среды разработки "в сети")|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (на 64-разрядном компьютере)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled — задайте для этого параметра значение 1, чтобы отключить доступ к содержимому справки в Интернете.|  
|Отключение управления содержимым|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (на 64-разрядном компьютере)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled — задайте значение 1 для отключения вкладки **Управление содержимым** в окне справки.|  
|Указание на хранилище локального содержимого в сетевой папке с общим доступом|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath="*ContentStoreNetworkShare*"|  
|Отключение установки содержимого при первом запуске возможности Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (на 64-разрядном компьютере)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection — задайте значение 1, чтобы отключить возможности справки, настраиваемые при первом запуске Visual Studio.|  
  
## <a name="see-also"></a>См. также  
 [Руководство администратора Help Viewer](../ide/help-viewer-administrator-guide.md)
