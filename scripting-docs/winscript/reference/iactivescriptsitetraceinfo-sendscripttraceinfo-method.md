---
title: Метод IActiveScriptSiteTraceInfo::SendScriptTraceInfo | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0419e4c5-eb7c-45a3-b6dc-1a5e157d95f9
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c2b444afa22e38694166f7d7522dbe6d0d3774d4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147683"
---
# <a name="iactivescriptsitetraceinfosendscripttraceinfo-method"></a>Метод IActiveScriptSiteTraceInfo::SendScriptTraceInfo
Отправляет сведения о трассировке, включающий тип события, контекст и оператора скрипта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT SendScriptTraceInfo(     [in] SCRIPTTRACEINFO stiEventType,     [in] GUID guidContextID,     [in] DWORD dwScriptContextCookie,     [in] LONG lScriptStatementStart,     [in] LONG lScriptStatementEnd,     [in] DWORD64 dwReserved );   
```  
  
#### <a name="parameters"></a>Параметры  
 `stiEventType`  
 Тип события.  
  
 `guidContextId`  
 Идентификатор GUID контекста.  
  
 `dwScriptContextCookie`  
 Файл cookie контекста.  
  
 `lScriptStatementStart`  
 Расположение начала выполнения инструкции скрипта.  
  
 `lScriptStatementEnd`  
 Расположение, в конце оператора скрипта.  
  
 `dwReserved`  
 Зарезервировано.