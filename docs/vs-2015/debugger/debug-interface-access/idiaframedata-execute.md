---
title: IDiaFrameData::execute | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f8949e0a9c0f7aac0a648df9de8ee50c4f32292c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49197773"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Выполняет развертывание стека и возвращает результаты в интерфейсе стека кадра стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)



