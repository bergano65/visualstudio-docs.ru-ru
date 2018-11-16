---
title: IDiaSession::findLinesByVA | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 74ec8935103120a274876bb6ca074d2f9b01df2b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744494"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает информация о номере строки для строк, содержащихся в указанный диапазон виртуальных адресов (VA).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `va`  
 [in] Указывает адрес как ва.  
  
 `length`  
 [in] Указывает число байтов из диапазона адресов, чтобы охватить с этим запросом.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , содержащий список всех строке номера, охватывают указанный диапазон адресов.  
  
## <a name="example"></a>Пример  
 В этом примере показана функция, получающий все номера строк, содержащихся в функции, используя функции виртуальный адрес и длину.  
  
```cpp#  
IDiaEnumLineNumbers *GetLineNumbersByVA(IDiaSymbol *pFunc, IDiaSession *pSession)  
{  
    IDiaEnumLineNumbers* pEnum = NULL;  
    ULONGLONG            va;  
    ULONGLONG            length;  
  
    if (pFunc->get_virtualAddress ( &va ) == S_OK)  
    {  
        pFunc->get_length( &length );  
        pSession->findLinesByVA( va, static_cast<DWORD>( length ), &pEnum );  
    }  
    return(pEnum);  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)



