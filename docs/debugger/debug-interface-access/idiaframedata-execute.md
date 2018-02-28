---
title: "IDiaFrameData::execute | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8ad08fd9800fdc197d4218fa55c83487e132f25d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Выполняет развертывание стека и возвращает результаты в интерфейсе обход кадра стека.  
  
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
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.  
  
|Значение|Описание:|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Не удается выполнить кадра стека в кода пролога.|  
|E_DIA_SYNTAX|Синтаксический анализ произошла ошибка в программе кадра.|  
|E_DIA_FRAME_ACCESS|Не удается регистры доступа или памяти.|  
|E_DIA_VALUE|Ошибка при вычислении значения (например, деление на ноль).|  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается во время отладки для очистки стека. [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) объект реализован клиентским приложением для получения обновлений в регистры и предоставлять методы, используемые `execute` метод.  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)