---
title: Коды ошибок Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- error codes, source control plug-ins
- source control plug-ins, error codes
- errors [Visual Studio SDK]
ms.assetid: d9cbd1c4-719b-467a-8100-333c1e146d3b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34072f6ddbd632f83dd308c6cb63427e02bb110b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711842"
---
# <a name="error-codes"></a>Коды ошибок
Когда функция Подключаемого к НиЮ в API элемента управления исходным кодом возвращает ошибку, ожидается, что она станет одним из следующих кодов ошибок. Все ошибки отрицательные, предупреждения или информационные коды ошибок являются положительными, и успех 0.

|Код ошибки|Значение|Описание|
|----------------|-----------|-----------------|
|`SCC_I_SHARESUBPROJOK`|7|Подключаемый модуль поддерживает добавление файлов из управления исходным ресурсом в два этапа. Для получения дополнительной [SccSetOption](../extensibility/sccsetoption-function.md)информации см.|
|`SCC_I_FILEDIFFERS`|6|Локальный файл отличается от файла в базе данных управления исходным кодом (например, [SccDiff](../extensibility/sccdiff-function.md) может вернуть это значение).|
|`SCC_I_RELOADFILE`|5|Локальный файл был изменен во время операции управления исходным источником; IDE должен перезагрузить файл, если это возможно.|
|`SCC_I_FILENOTAFFECTED`|4|Файл не влияет.|
|`SCC_I_PROJECTCREATED`|3|Проект был создан во время операции управления исходным кодом (например, во время вызова [в SccOpenProject,](../extensibility/sccopenproject-function.md) когда `SCC_OP_CREATEIFNEW` указан флаг).|
|`SCC_I_OPERATIONCANCELED`|2|Операция отменена.|
|`SCC_I_ADV_SUPPORT`|1|Подключаемый модуль поддерживает расширенные параметры для указанной команды. Для получения дополнительной информации [см.](../extensibility/sccgetcommandoptions-function.md)|
|`SCC_OK`|0|Успешно.|
|`SCC_E_INITIALIZEFAILED`|-1|Ошибка: инициализация не удалась.|
|`SCC_E_UNKNOWNPROJECT`|-2|Ошибка: проект неизвестен.|
|`SCC_E_COULDNOTCREATEPROJECT`|–3|Ошибка: проект не может быть создан.|
|`SCC_E_NOTCHECKEDOUT`|–4|Ошибка: файл не выявляется.|
|`SCC_E_ALREADYCHECKEDOUT`|-5|Ошибка: файл уже проверен.|
|`SCC_E_FILEISLOCKED`|-6|Ошибка: файл заблокирован.|
|`SCC_E_FILEOUTEXCLUSIVE`|-7|Ошибка: файл проверяется исключительно.|
|`SCC_E_ACCESSFAILURE`|–8|Возникла проблема с доступом к системе управления исходным кодом, вероятно, из-за проблем с сетью или раздором. Рекомендуется повторная попытка.|
|`SCC_E_CHECKINCONFLICT`|–9|Ошибка: во время регистрации произошел конфликт.|
|`SCC_E_FILEALREADYEXISTS`|–10|Ошибка: файл уже существует.|
|`SCC_E_FILENOTCONTROLLED`|-11|Ошибка: файл не находится под контролем источника.|
|`SCC_E_FILEISCHECKEDOUT`|-12|Ошибка: файл проверен.|
|`SCC_E_NOSPECIFIEDVERSION`|-13|Ошибка: нет указанной версии.|
|`SCC_E_OPNOTSUPPORTED`|-14|Ошибка: операция не поддерживается.|
|`SCC_E_NONSPECIFICERROR`|-15|Неспецифическая ошибка.|
|`SCC_E_OPNOTPERFORMED`|-16|Ошибка, операция не была выполнена.|
|`SCC_E_TYPENOTSUPPORTED`|-17|Ошибка: тип файла, например, двоичный, не поддерживается системой управления исходным кодом.|
|`SCC_E_VERIFYMERGE`|–18|Файл был автоматически объединен, но не был проверен, поскольку он находится на рассмотрении проверки пользователя.|
|`SCC_E_FIXMERGE`|-19|Файл был автоматически объединен, но не был зарегистрирован из-за конфликта слияния, который должен быть решен вручную.|
|`SCC_E_SHELLFAILURE`|–20|Ошибка из-за отказа оболочки.|
|`SCC_E_INVALIDUSER`|-21|Ошибка: пользователь недействителен.|
|`SCC_E_PROJECTALREADYOPEN`|-22|Ошибка: проект уже открыт.|
|`SCC_E_PROJSYNTAXERR`|-23|Ошибка синтаксиса проекта.|
|`SCC_E_INVALIDFILEPATH`|-24|Ошибка: путь файла недействителен.|
|`SCC_E_PROJNOTOPEN`|-25|Ошибка: проект не открыт.|
|`SCC_E_NOTAUTHORIZED`|-26|Ошибка: пользователь не уполномочен выполнять эту операцию.|
|`SCC_E_FILESYNTAXERR`|-27|Ошибка синтаксиса файлов.|
|`SCC_E_FILENOTEXIST`|-28|Ошибка, локальный файл не существует.|
|`SCC_E_CONNECTIONFAILURE`|-29|Ошибка: произошел сбой соединения.|
|`SCC_E_UNKNOWNERROR`|–30|Неизвестная ошибка.|
|`SCC_E_BACKGROUNDGETINPROGRESS`|-31|Фоновая операция получения в настоящее время продолжается.|

## <a name="macros-provided-for-quick-checking"></a>Макрос предусмотрено для быстрой проверки

```cpp
IS_SCC_ERROR(rtn) (((rtn) < 0) ? TRUE : FALSE)
IS_SCC_SUCCESS(rtn) (((rtn) == SCC_OK) ? TRUE : FALSE)
IS_SCC_WARNING(rtn) (((rtn) > 0) ? TRUE : FALSE)
```

## <a name="remarks"></a>Примечания
 Все функции Подключаемого aPI управления исходным управлением (кроме [SccAdd,](../extensibility/sccadd-function.md) [SccCheckin](../extensibility/scccheckin-function.md)и [SccDiff),](../extensibility/sccdiff-function.md)как ожидается, увенчаются успехом, когда локальные файлы, которые передаются в качестве аргументов, не существуют в рабочей папке. Например, IDE может выдавать вызов [в SccCheckout](../extensibility/scccheckout-function.md) или [SccUncheckout](../extensibility/sccuncheckout-function.md) в файле, который не существует в рабочей папке, но существует в системе управления исходным источником. Этот призыв увенчается успехом. Только при отсутствии файла в рабочей папке или в системе управления исходным источником функция, как ожидается, сбой.

 Некоторые функции, `SccAdd` `SccCheckin`такие как `SCC_E_FILENOTEXIST` и, должны конкретно возвращаться, когда файл в рабочей папке не существует. Другие функции должны быть успешными, если рабочий файл не существует, если функции работают на действительное имя файла в системе управления исходным источником.

 Плагин управления исходным элементом не должен делать никаких предположений относительно привилегий в файле в рабочей папке, даже если плагин пометил файл, прочитаный только во время некоторой операции. Файл в рабочей папке может быть перемещен, удален и изменен вне элемента управления плагина.

## <a name="see-also"></a>См. также
- [Плагины управления исходным элементом](../extensibility/source-control-plug-ins.md)
