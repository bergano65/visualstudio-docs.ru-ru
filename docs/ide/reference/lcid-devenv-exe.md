---
title: "-LCID (devenv.exe) | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aa33b329002991c5629f3d48361c6f4fa3c694e0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
Задает язык по умолчанию, используемый для текста, валюты и других значений в интегрированной среде разработки (IDE).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Аргументы  
 `LocaleID`  
 Обязательный. Код языка (LCID) для заданного вами языка.  
  
## <a name="remarks"></a>Примечания  
 Загружает интегрированную среду разработки и устанавливает естественный язык по умолчанию для среды. Это изменение сохраняется между сеансами и отражается в области **Язык интерфейса** параметров **Среда** диалогового окна **Параметры** в интегрированной среде разработки.  
  
 Если указанный язык недоступен в системе пользователя, параметр /LCID игнорируется.  
  
 В приведенной ниже таблице перечислены коды языка, поддерживаемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Язык|Код языка|  
|--------------|----------|  
|Китайский (упрощенный)|2052|  
|Китайский (традиционное письмо)|1028|  
|английский|1033|  
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