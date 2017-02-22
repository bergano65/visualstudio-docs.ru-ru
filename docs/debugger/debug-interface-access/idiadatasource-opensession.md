---
title: "IDiaDataSource::openSession | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::openSession - метод"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Открывает сеанс для запросов символы.  
  
## Синтаксис  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### Параметры  
 ppSession  
 \[out\] возвращает [IDiaSession](../../debugger/debug-interface-access/idiasession.md) объект, представляющий первый сеанс.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  В следующей таблице приведены возможные возвращаемые значения для данного метода.  
  
|Значение|Описание|  
|--------------|--------------|  
|E\_UNEXPECTED|[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) объект, который ранее не был инициализирован с источником символов.|  
|E\_INVALIDARG|Недопустимо `ppSession` параметр.|  
|E\_OUTOFMEMORY|Недостаточно памяти, чтобы открыть сеанс.|  
  
## Заметки  
 Этот метод открывает [IDiaSession](../../debugger/debug-interface-access/idiasession.md) объект источника данных.  
  
 `IDiaSession` функциональные запросы объектов в источник данных.  Сеанс управляет одно адресное пространство для каждого набора символов отладки.  Если exe\- или dll\-файла, описанные символами источника данных активны в разных диапазонах адресов \(например, потому, что несколько процессов имеют загруженный него\), то один сеанс для каждого диапазона адресов следует использовать.  
  
## Пример  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Обзор](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Запрос PDB\-файла](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)