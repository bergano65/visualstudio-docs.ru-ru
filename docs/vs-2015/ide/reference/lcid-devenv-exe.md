---
title: -LCID (devenv.exe) | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e84d02cef1c1a22fdcbfc6396037e54e2b8981b4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568955"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [- LCID (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/lcid-devenv-exe).  
  
  
Задает язык по умолчанию, используемый для текста, валюты и других значений в интегрированной среде разработки (IDE).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Аргументы  
 `LocaleID`  
 Обязательно. Код языка (LCID) для заданного вами языка.  
  
## <a name="remarks"></a>Примечания  
 Загружает интегрированную среду разработки и устанавливает естественный язык по умолчанию для среды. Это изменение сохраняется между сеансами и отражается в области **Язык интерфейса** параметров **Среда** диалогового окна **Параметры** в интегрированной среде разработки.  
  
 Если указанный язык недоступен в системе пользователя, параметр /LCID игнорируется.  
  
 В приведенной ниже таблице перечислены коды языка, поддерживаемые [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Язык|LCID|  
|--------------|----------|  
|Китайский (упрощенное письмо)|2052|  
|Китайский (традиционное письмо)|1028|  
|Английский|1033|  
|Французский|1036|  
|Немецкий|1031|  
|Итальянский|1040|  
|Японский|1041|  
|Корейский|1042|  
|Испанский|3082|  
  
## <a name="example"></a>Пример  
 Этот пример загружает интегрированную среду разработки с английскими строками ресурсов.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>См. также  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Страница "Язык интерфейса", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md)



