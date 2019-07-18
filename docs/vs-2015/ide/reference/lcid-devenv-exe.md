---
title: -LCID (devenv.exe) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 0b1d83cca1da917a08b8765dae66fb240ca1dc75
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661013"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>См. также раздел  
 [Параметры командной строки для команды Devenv](../../ide/reference/devenv-command-line-switches.md)   
 [Страница "Язык интерфейса", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Настройка макетов окон](../../ide/customizing-window-layouts-in-visual-studio.md)
