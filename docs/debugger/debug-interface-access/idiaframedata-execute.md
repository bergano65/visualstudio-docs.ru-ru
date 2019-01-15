---
title: IDiaFrameData::execute | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6be6c631f9ea0db47829f305f90bd1c296de2f28
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53958751"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Выполняет развертывание стека и возвращает результаты в интерфейсе стека кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `frame`  
 [in] [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) объект, содержащий состояние регистров кадра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Не удается выполнить кадр стека в код пролога.|  
|E_DIA_SYNTAX|Выполните синтаксический анализ ошибка в программе кадра.|  
|E_DIA_FRAME_ACCESS|Не удалось регистры доступа или памяти.|  
|E_DIA_VALUE|Ошибка при вычислении значения (например, деление на ноль).|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается во время отладки для раскручивания стека. [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) объект реализуется клиентским приложением для получения обновлений в регистры и сообщать о способах, используемых `execute` метод.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)