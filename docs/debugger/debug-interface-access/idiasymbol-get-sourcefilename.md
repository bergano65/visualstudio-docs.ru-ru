---
title: IDiaSymbol::get_sourceFileName | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_sourceFileName method
ms.assetid: 0f5dce88-829e-4df3-8acd-8d71076ad167
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4cddf0be9982b8b8e2e6914c3c91230bfb315f14
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetsourcefilename"></a>IDiaSymbol::get_sourceFileName
Возвращает имя файла объекта компиляции исходного файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_sourceFileName (   
   BSTR* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает имя файла объекта компиляции исходного файла.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)