---
title: 'Идиадатасаурце:: Опенсессион | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198605"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает сеанс для запроса символов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 ппсессион  
 заполняет Возвращает объект [IDiaSession](../../debugger/debug-interface-access/idiasession.md) , представляющий открытый сеанс.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_UNEXPECTED|Объект [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md) ранее не был инициализирован с источником символов.|  
|E_INVALIDARG|Недопустимый параметр `ppSession`.|  
|E_OUTOFMEMORY|Недостаточно памяти для открытия сеанса.|  
  
## <a name="remarks"></a>Remarks  
 Этот метод открывает объект [IDiaSession](../../debugger/debug-interface-access/idiasession.md) для источника данных.  
  
 `IDiaSession` объекты реализуют запросы к источнику данных. Сеанс управляет одним адресным пространством для каждого набора отладочных символов. Если файл exe или DLL, описываемый символами источника данных, активен в нескольких диапазонах адресов (например, из-за загрузки нескольких процессов), следует использовать один сеанс для каждого диапазона адресов.  
  
## <a name="example"></a>Пример  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md)   
 [Средств](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Запрос PDB-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
