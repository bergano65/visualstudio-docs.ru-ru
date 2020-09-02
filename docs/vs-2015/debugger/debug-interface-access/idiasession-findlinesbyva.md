---
title: 'IDiaSession:: Финдлинесбива | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findLinesByVA method
ms.assetid: f647eee9-a73c-483b-9fe9-21f42e560a7b
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ca69acebc9710bc18cba39ea9998bf90d2bf5767
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151648"
---
# <a name="idiasessionfindlinesbyva"></a>IDiaSession::findLinesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает сведения о номере строки для строк, содержащихся в указанном диапазоне виртуальных адресов (ва).  
  
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
 окне Указывает адрес в виде ва.  
  
 `length`  
 окне Указывает число байтов диапазона адресов, которое будет охватывать этот запрос.  
  
 `ppResult`  
 заполняет Возвращает объект [идиаенумлиненумберс](../../debugger/debug-interface-access/idiaenumlinenumbers.md) , содержащий список всех номеров строк, охватывающих указанный диапазон адресов.  
  
## <a name="example"></a>Пример  
 В этом примере показана функция, которая получает все номера строк, содержащиеся в функции, с использованием виртуального адреса и длины функции.  
  
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
  
## <a name="see-also"></a>См. также:  
 [идиаенумлиненумберс](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
