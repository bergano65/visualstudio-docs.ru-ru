---
title: 'Идиадатасаурце:: Лоадандвалидатедатафромпдб | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f19a910af45ed70ae74c72441890ecae6c81d2a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198623"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Открывает и проверяет, совпадает ли файл базы данных программы (PDB) с предоставленными сведениями о сигнатуре, и готовит PDB-файл в качестве источника данных отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT loadAndValidateDataFromPdb (   
   LPCOLESTR pdbPath,  
   GUID*     pcsig70,  
   DWORD     sig,  
   DWORD     age  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdbPath`  
 окне Путь к PDB-файлу.  
  
 `pcsig70`  
 окне Подпись GUID для проверки на соответствие с подписью PDB-файла. Только PDB-файлы в [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] и более поздних версиях имеют сигнатуры GUID.  
  
 `sig`  
 окне 32-разрядная сигнатура, которую необходимо проверить на соответствие с заданной сигнатурой PDB-файла.  
  
 `age`  
 окне Значение age для проверки. Возраст не обязательно соответствует ни одному известному значению времени, он используется, чтобы определить, не синхронизирован ли PDB-файл с соответствующим exe-файлом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки. В следующей таблице показаны возможные возвращаемые значения для этого метода.  
  
|Значение|Описание|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|Не удалось открыть файл, или файл имеет недопустимый формат.|  
|E_PDB_FORMAT|Попытка доступа к файлу с устаревшим форматом.|  
|E_PDB_INVALID_SIG|Сигнатура не совпадает.|  
|E_PDB_INVALID_AGE|Возраст не соответствует.|  
|E_INVALIDARG|Недопустимый параметр.|  
|E_UNEXPECTED|Источник данных уже подготовлен.|  
  
## <a name="remarks"></a>Remarks  
 PDB-файл содержит как сигнатуры, так и возрастные значения. Эти значения реплицируются в exe-или DLL-файл, соответствующий PDB-файлу. Перед тем как подготовить источник данных, этот метод проверяет, совпадают ли сигнатура и возраст именованного PDB-файла с указанными значениями.  
  
 Чтобы загрузить PDB-файл без проверки, используйте метод [идиадатасаурце:: лоаддатафромпдб](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Чтобы получить доступ к процессу загрузки данных (посредством механизма обратного вызова), используйте метод [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Чтобы загрузить PDB-файл непосредственно из памяти, используйте метод [идиадатасаурце:: лоаддатафромистреам](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## <a name="example"></a>Пример  
  
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
  
## <a name="see-also"></a>См. также:  
 [идиадатасаурце](../../debugger/debug-interface-access/idiadatasource.md)   
 [Идиадатасаурце:: Лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [Идиадатасаурце:: Лоаддатафромпдб](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
