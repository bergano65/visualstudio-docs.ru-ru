---
title: 'IDiaFrameData:: Execute | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4042cf58ee34b5f49df601b94e1110f03e0b6f5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197550"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Выполняет очистку стека и возвращает результаты в интерфейсе кадра обхода стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT execute (   
   IDiaStackWalkFrame* frame  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `frame`  
 окне Объект [идиастакквалкфраме](../../debugger/debug-interface-access/idiastackwalkframe.md) , содержащий состояние регистров кадров.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_DIA_INPROLOG|Невозможно выполнить кадр стека в коде пролога.|  
|E_DIA_SYNTAX|Ошибка синтаксического анализа, обнаруженная в рамке программы.|  
|E_DIA_FRAME_ACCESS|Не удается получить доступ к регистрам или памяти.|  
|E_DIA_VALUE|Ошибка при вычислении значения (например, деление на ноль).|  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается во время отладки для очистки стека. Объект [идиастакквалкфраме](../../debugger/debug-interface-access/idiastackwalkframe.md) реализуется клиентским приложением для получения обновлений регистров и для предоставления методов, используемых `execute` методом.  
  
## <a name="see-also"></a>См. также:  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
