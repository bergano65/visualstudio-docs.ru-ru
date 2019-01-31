---
title: IDiaSession::findFileById | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c97df0a5c860fa27fdc136164b9fea79f58fa26
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042144"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
Извлекает исходный файл, идентификатор файла источника.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `uniqueId`  
 [in] Задает идентификатор исходного файла.  
  
 `ppResult`  
 [out] Возвращает [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) извлечь объект, представляющий исходный файл.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Идентификатор файла источника — это уникальное значение, используется внутренним образом для пакета SDK для доступа к интерфейсу отладки, чтобы сделать уникальным все исходные файлы. Этот метод обычно используется внутренне для пакета SDK для доступа к интерфейсу отладки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)