---
title: 'IDiaSession:: Финдлинес | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4cf6ff2f1484255fc6c535ce764a5c6335161b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151677"
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает номера строк в указанных компилируемого объекта и идентификаторах исходных файлов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `compiland`  
 окне Объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий компилируемого объекта. Используйте этот интерфейс в качестве контекста для поиска номеров строк.  
  
 `file`  
 окне Объект [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) , представляющий исходный файл, в котором выполняется поиск номеров строк.  
  
 `ppResult`  
 заполняет Возвращает объект [идиаенумлиненумберс](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , содержащий список полученных номеров строк.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [идиаенумлиненумберс](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
