---
title: IDiaSession::findFile | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09e346ca82e813e8b93ad58ab81da4a70951e9f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
Извлекает исходные файлы, компилируемого объекта и имя.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCompiland`  
 [in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий компилируемого объекта для использования в качестве контекста для поиска. Присвойте этому параметру значение `NULL` для поиска исходных файлов во всех компилируемых объектах.  
  
 `name`  
 [in] Задает имя исходного файла, который требуется получить. Присвойте этому параметру значение `NULL` для всех исходных файлов требуется получить.  
  
 `option`  
 [in] Задает параметры сравнения, который применяется для поиска имени. Значения из [NameSearchOptions-перечисление](../../debugger/debug-interface-access/namesearchoptions.md) перечисления может использоваться отдельно или в сочетании.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) извлечь объект, содержащий список исходных файлов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="example"></a>Пример  
  
```C++  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)