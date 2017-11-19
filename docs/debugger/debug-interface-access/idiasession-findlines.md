---
title: "IDiaSession::findLines | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSession::findLines method
ms.assetid: d6e84916-fd55-457e-b057-57f97b51fe73
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 366c41ee6befafa633428e2b6a959809a08b6cd9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindlines"></a>IDiaSession::findLines
Возвращает номера строк в указанной компилируемого объекта и идентификаторы исходного файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findLines (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `compiland`  
 [in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий компилируемого объекта. Этот интерфейс можно используйте как контекст, в котором для поиска номера строк.  
  
 `file`  
 [in] [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) объект, представляющий исходный файл, в котором выполняется поиск для номеров строк.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) извлечь объект, содержащий список номеров строк.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)