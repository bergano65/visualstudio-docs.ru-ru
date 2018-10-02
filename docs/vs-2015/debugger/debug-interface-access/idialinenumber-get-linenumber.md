---
title: IDiaLineNumber::get_lineNumber | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
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
- IDiaLineNumber::get_lineNumber method
ms.assetid: 2dff3fd9-097d-4645-bc1b-cb65ecbc42a6
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4718642a7197cd5258210f78f0457fb902dcd1c9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569079"
---
# <a name="idialinenumbergetlinenumber"></a>IDiaLineNumber::get_lineNumber
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaLineNumber::get_lineNumber](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idialinenumber-get-linenumber).  
  
Получает номер строки в исходном файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_lineNumber (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает номер строки в исходном файле.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`. Возвращает `S_FALSE` Если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="example"></a>Пример  
  
```cpp#  
CComPtr< IDiaLineNumber> pLine;  
DWORD linenum;  
pLine->get_lineNumber( &linenum );  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)



