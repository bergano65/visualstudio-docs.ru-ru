---
title: 'IDiaSession:: Финдфилебид | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFileById method
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c57072d4b8707136f0ccd2a759bc3d393720efb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150439"
---
# <a name="idiasessionfindfilebyid"></a>IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает исходный файл по идентификатору исходного файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `uniqueId`  
 окне Указывает идентификатор исходного файла.  
  
 `ppResult`  
 заполняет Возвращает объект [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , представляющий извлеченный исходный файл.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Идентификатор исходного файла — это уникальное значение, используемое внутренним образом для пакета SDK DIA, чтобы сделать все исходные файлы уникальными. Этот метод обычно используется внутри пакета SDK DIA.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession:: Финдфиле](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
