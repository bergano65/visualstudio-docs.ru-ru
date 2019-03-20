---
title: Метод IActiveScriptSiteUIControl::GetUIBehavior | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9a944335-856a-4c6b-b2bc-8872542941b7
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e3f6247afc70ef1197ea759ffdf475c2d6c0a0c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158218"
---
# <a name="iactivescriptsiteuicontrolgetuibehavior-method"></a>Метод IActiveScriptSiteUIControl::GetUIBehavior
Получает [перечисление SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md) , представляющий способ обработки элемент управления пользовательского интерфейса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT GetUIBehavior(     [in] SCRIPTUICITEM UicItem,     [out] SCRIPTUICHANDLING * pUicHandling );   
```  
  
#### <a name="parameters"></a>Параметры  
 `UicItem`  
 Тип элемента управления.  
  
 `pUicHandling`  
 Способ управления должны обрабатываться.