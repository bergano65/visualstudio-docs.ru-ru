---
title: Интерфейс IActiveScriptWinRTErrorDebug | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 52e7728b4143231912227e5e55faa5eef01b7490
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63425789"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug — интерфейс
Реализуется обработчиком JavaScript для предоставления расширенных сведений об ошибке среды выполнения Windows из [перечисление BREAKREASON](../../winscript/reference/breakreason-enumeration.md) событий. Можно выполнить QueryInterface для получения их из [iactivescripterror —](../../winscript/reference/iactivescripterror.md) объекта.  
  
> [!IMPORTANT]
> Этот интерфейс реализуется в PDM v11.0 и более поздней версии. Обнаружено в activdbg100.h.  
  
## <a name="methods"></a>Методы  
 Интерфейс `IActiveScriptWinRTErrorDebug` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|Возвращает возможности SID для ошибки среды выполнения Windows, если он доступен.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|Возвращает среды выполнения Windows только ошибки строку ссылки, если он доступен.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|Возвращает среды выполнения Windows только строка ошибки, если он доступен.|