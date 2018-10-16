---
title: Коды ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 220d53db343a90f6e19e0f365c621cbf55186a8c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189986"
---
# <a name="error-codes"></a>Коды ошибок
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функции API подключаемого модуля управления источника возвращает ошибку, ожидается один из следующих кодов ошибки. Все ошибки имеет отрицательное значение, предупреждения или информационные коды являются положительными, и 0 — успех.  
  
|Код ошибки|Значение|Описание|  
|----------------|-----------|-----------------|  
|`SCC_I_SHARESUBPROJOK`|7|Подключаемый модуль поддерживает добавление файлов из системы управления версиями в два этапа. Дополнительные сведения см. в разделе [SccSetOption](../extensibility/sccsetoption-function.md).|  
|`SCC_I_FILEDIFFERS`|6|Локального файла отличается от файла в базе данных управления версиями (например, [SccDiff](../extensibility/sccdiff-function.md) могут возвращать это значение).|  
|`SCC_I_RELOADFILE`|5|Локальный файл был изменен во время операция управления версиями; по возможности интегрированной среды разработки следует перезагрузить файл.|  
|`SCC_I_FILENOTAFFECTED`|4|Файл не изменяется.|  
|`SCC_I_PROJECTCREATED`|3|Проект был создан во время операции системы управления версиями (например, во время вызова [SccOpenProject](../extensibility/sccopenproject-function.md) при `SCC_OP_CREATEIFNEW` установлен флаг).|  
|`SCC_I_OPERATIONCANCELED`|2|Операция была отменена.|  
|`SCC_I_ADV_SUPPORT`|1|Подключаемый модуль поддерживает дополнительные параметры для заданной команды. Дополнительные сведения см. в разделе [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md).|  
|`SCC_OK`|0|Выполнено.|  
|`SCC_E_INITIALIZEFAILED`|-1|Ошибка: Сбой при инициализации.|  
|`SCC_E_UNKNOWNPROJECT`|-2|Ошибка: неизвестный проект.|  
|`SCC_E_COULDNOTCREATEPROJECT`|-3|Ошибка: не удалось создать проект.|  
|`SCC_E_NOTCHECKEDOUT`|-4|Ошибка: файл не извлечен.|  
|`SCC_E_ALREADYCHECKEDOUT`|-5|Ошибка: файл уже извлечен.|  
|`SCC_E_FILEISLOCKED`|-6|Ошибка: файл заблокирован.|  
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Ошибка: файл извлечен монопольном режиме.|  
|`SCC_E_ACCESSFAILURE`|-8|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|`SCC_E_CHECKINCONFLICT`|-9|Ошибка: произошел конфликт при возврате.|  
|`SCC_E_FILEALREADYEXISTS`|-10|Ошибка: файл уже существует.|  
|`SCC_E_FILENOTCONTROLLED`|-11|Ошибка: файл не в системе управления версиями.|  
|`SCC_E_FILEISCHECKEDOUT`|-12|Ошибка: файл извлечен.|  
|`SCC_E_NOSPECIFIEDVERSION`|-13|Ошибка: отсутствует указанный версия.|  
|`SCC_E_OPNOTSUPPORTED`|-14|Ошибка: операция не поддерживается.|  
|`SCC_E_NONSPECIFICERROR`|-15|Обнаружена неспецифическая ошибка.|  
|`SCC_E_OPNOTPERFORMED`|-16|Ошибка, операция не выполнена.|  
|`SCC_E_TYPENOTSUPPORTED`|-17|Ошибка: тип файла, например, двоичных данных, не поддерживается системы управления исходным кодом.|  
|`SCC_E_VERIFYMERGE`|-18|Файл был автоматически объединены, но еще не возвращен, так как он выполняется проверка ожидающих пользователей.|  
|`SCC_E_FIXMERGE`|-19|Файл был автоматически объединены, но еще не возвращен из-за конфликта слияния, который необходимо разрешить вручную.|  
|`SCC_E_SHELLFAILURE`|-20|Ошибка из-за сбоя оболочки.|  
|`SCC_E_INVALIDUSER`|-21|Ошибка: недопустимый пользователь.|  
|`SCC_E_PROJECTALREADYOPEN`|-22|Ошибка: проект уже открыт.|  
|`SCC_E_PROJSYNTAXERR`|-23|Синтаксическая ошибка проекта.|  
|`SCC_E_INVALIDFILEPATH`|-24|Ошибка: недопустимый путь к файлу.|  
|`SCC_E_PROJNOTOPEN`|-25|Ошибка: проект не открыт.|  
|`SCC_E_NOTAUTHORIZED`|-26|Ошибка: пользователь не авторизован для выполнения этой операции.|  
|`SCC_E_FILESYNTAXERR`|-27|Синтаксическая ошибка: файл.|  
|`SCC_E_FILENOTEXIST`|-28|Ошибка, локальный файл не существует.|  
|`SCC_E_CONNECTIONFAILURE`|-29|Ошибка: произошел сбой подключения.|  
|`SCC_E_UNKNOWNERROR`|-30|Неизвестная ошибка.|  
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Фоновая операция get данный момент выполняется.|  
  
## <a name="macros-provided-for-quick-checking"></a>Макросы для быстрого проверки  
  
```cpp#  
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)  
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)  
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)  
```  
  
## <a name="remarks"></a>Примечания  
 Все функции API подключаемого модуля управления источника (за исключением [SccAdd](../extensibility/sccadd-function.md), [SccCheckin](../extensibility/scccheckin-function.md), и [SccDiff](../extensibility/sccdiff-function.md)) ожидается успешное выполнение, если локальные файлы, которые передаются как аргументы не существует в рабочей папке. Например, интегрированной среды разработки может выдать вызов [SccCheckout](../extensibility/scccheckout-function.md) или [SccUncheckout](../extensibility/sccuncheckout-function.md) в файле, который не существует в рабочей папке, но существует в системе управления версиями. Этот вызов пройдет успешно. Только в том случае, если файл отсутствует в рабочей папке или в системе управления версиями функция должна завершиться ошибкой.  
  
 Некоторые функции, такие как `SccAdd` и `SccCheckin`, в частности должен возвращать `SCC_E_FILENOTEXIST` при файл в рабочей папке не существует. Другие функции ожидается успешное выполнение при рабочего файла не существует, если функции выполняются на допустимое имя файла в системе управления версиями.  
  
 Подключаемый модуль системы управления версиями следует делать никаких предположений о правах доступа на файл в рабочую папку, даже если подключаемый модуль пометили файл только для чтения во время некоторой операции. В рабочей папке файл можно переместить, удаленные и изменена за пределами plug в элемент управления.  
  
## <a name="see-also"></a>См. также  
 [Подключаемые модули системы управления версиями](../extensibility/source-control-plug-ins.md)

