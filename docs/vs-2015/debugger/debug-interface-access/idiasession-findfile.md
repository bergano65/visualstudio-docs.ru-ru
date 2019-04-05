---
title: IDiaSession::findFile | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findFile method
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1e791bc09ba3dd4f1811c650926eadb0f7f0462a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991058"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает исходные файлы, компилируемого объекта и имя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pCompiland`  
 [in] [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий единице компиляции для использования в качестве контекста для поиска. Присвойте этому параметру значение `NULL` поиска исходных файлов во всех компилируемых объектах.  
  
 `name`  
 [in] Задает имя исходного файла, который требуется получить. Присвойте этому параметру значение `NULL` для всех исходных файлов требуется получить.  
  
 `option`  
 [in] Задает параметры сравнения, который применяется для поиска имени. Значения из [перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) перечисления можно использовать отдельно или в сочетании.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) извлечь объект, содержащий список исходных файлов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
