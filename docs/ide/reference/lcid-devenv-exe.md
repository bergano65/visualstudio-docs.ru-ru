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
ms.workload: multiple
ms.openlocfilehash: bdc04655ccfc8ca5f6c1e45e4378f15221b99f4c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
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
  
 В приведенной ниже таблице перечислены коды языка, поддерживаемые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
|Язык|Код языка|  
|--------------|----------|  
|Китайский (упрощенное письмо)|2052|  
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