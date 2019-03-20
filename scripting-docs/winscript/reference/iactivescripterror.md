---
title: Iactivescripterror — | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ca783e2100fe74ed05499f9611a9b8f3399817f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144424"
---
# <a name="iactivescripterror"></a>IActiveScriptError
Объект, реализующий этот интерфейс передается [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) метод всякий раз, когда обработчик скриптов сталкивается с необработанной ошибкой. Затем узел вызывает методы этого объекта для получения сведений о возникшей ошибке.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Извлекает сведения об ошибке.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Извлекает расположение в исходном коде, где произошла ошибка.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Извлекает строки в исходном файле, где произошла ошибка.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейсы активных скриптов](../../winscript/reference/active-script-interfaces.md)