---
title: "IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "IDiaDataSource::loadAndValidateDataFromPdb - метод"
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Открывает и проверяет, что файл базы данных программы \(pdb\) соответствует предоставленным данным о подписи и подготавливает pdb\-файл в качестве источника данных отладки.  
  
## Синтаксис  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### Параметры  
 `pdbPath`  
 \[in\] путь к файлу pdb.  
  
 `pcsig70`  
 \[in\] идентификатор GUID подпись, подлежащая проверке подписи для файла pdb.  Только pdb\-файлы in [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] и более поздние версии имеют подписи GUID.  
  
 `sig`  
 \[in\] 32 \(sp2\) подпись, подлежащая проверке подписи для файла pdb.  
  
 `age`  
 \[in\] значение age, который требуется проверить.  Длительность не обязательно соответствует любое известное значение времени, него используется для определения если pdb\-файл из синхронизации с соответствующим exe\-файла.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  В следующей таблице приведены возможные возвращаемые значения для данного метода.  
  
|Значение|Описание|  
|--------------|--------------|  
|E\_PDB\_NOT\_FOUND|Не удалось открыть файл или же файл имеет недопустимый формат.|  
|E\_PDB\_FORMAT|Предпринята попытка получить доступ к файлу с устаревшими форматом.|  
|E\_PDB\_INVALID\_SIG|Сигнатура не совпадает.|  
|E\_PDB\_INVALID\_AGE|Age.|  
|E\_INVALIDARG|Недопустимый параметр.|  
|E\_UNEXPECTED|Источник данных уже был подготовлен.|  
  
## Заметки  
 Pdb\-файл содержит и сигнатурой и значения длительности.  Эти значения будут реплицированы в exe\- или dll\-файла, соответствующий файлу pdb.  Подготовка источника данных, прежде чем этот метод проверяет, что подпись и длительность pdb\-файла с именами соответствующих предоставленным значения.  
  
 Чтобы загрузить файл pdb без проверки, используйте [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) метод.  
  
 Чтобы получить доступ к процессу загрузки данных \(через механизм обратного вызова, используйте\) [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) метод.  
  
 Чтобы загрузить файл pdb непосредственно из памяти, используйте [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md) метод.  
  
## Пример  
  
```cpp#  
IDiaDataSource* pSource;  // Previously created data source.  
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);  
DWORD expectedFileSignature = 0x12345678;  
DWORD expectedAge           = 128;  
  
HRESULT hr;  
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",  
                                          &expectedGUIDSignature,  
                                          expectedFileSignature,  
                                          expectedAge);  
if (FAILED(hr))  
{  
    // Report an error  
}  
  
```  
  
## См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../Topic/IDiaDataSource::loadDataFromIStream.md)