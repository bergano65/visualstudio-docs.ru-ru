---
title: 'IDiaLineNumber:: get_lineNumber | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_lineNumber method
ms.assetid: 2dff3fd9-097d-4645-bc1b-cb65ecbc42a6
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0926c7805ac2deee5851627a764acfdea2f65cdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152052"
---
# <a name="idialinenumberget_linenumber"></a>IDiaLineNumber::get_lineNumber
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает номер строки в исходном файле.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_lineNumber (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 заполняет Возвращает номер строки в исходном файле.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="example"></a>Пример  
  
```cpp#  
CComPtr< IDiaLineNumber> pLine;  
DWORD linenum;  
pLine->get_lineNumber( &linenum );  
```  
  
## <a name="see-also"></a>См. также:  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
