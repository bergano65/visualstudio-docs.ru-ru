---
title: 'IDiaSession:: Финдфиле | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431645"
---
# <a name="idiasessionfindfile"></a>IDiaSession::findFile
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает исходные файлы по компилируемого объекта и имени.  
  
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
 окне Объект [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий компилируемого объекта, который будет использоваться в качестве контекста для поиска. Задайте для этого параметра значение `NULL` , чтобы найти исходные файлы во всех компиляндов.  
  
 `name`  
 окне Указывает имя исходного файла, который необходимо получить. Задайте для этого параметра значение, чтобы `NULL` получить все исходные файлы, которые будут извлечены.  
  
 `option`  
 окне Задает параметры сравнения, применяемые к поиску имен. Значения из перечисления [перечисления намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать отдельно или в сочетании.  
  
 `ppResult`  
 заполняет Возвращает объект [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) , содержащий список извлекаемых исходных файлов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="example"></a>Пример  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## <a name="see-also"></a>См. также:  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
