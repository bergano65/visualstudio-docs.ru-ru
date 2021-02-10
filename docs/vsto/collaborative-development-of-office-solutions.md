---
title: Совместная разработка решений Office
description: Узнайте, как несколько разработчиков могут работать над проектом Office так же, как они совместно работают над другими проектами Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 028530014afdc78ab6c9c0483c3d443195383793
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942312"
---
# <a name="collaborative-development-of-office-solutions"></a>Совместная разработка решений Office
  Несколько разработчиков могут работать над проектом Office так же, как они совместно работают над другими проектами Visual Studio. Visual Studio правильно обнаруживает Microsoft Office установки на каждом компьютере, даже если Office установлен в разных расположениях. Однако следует учитывать некоторые важные моменты.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Свойства отладки не являются общими
 Отладка свойств не выполняется для всех пользователей, зарегистрированных в системе контроля версий, одновременно. Visual Basic и проекты Visual C# хранят свойства отладки в файле, определенном пользователем (*имяПроекта*. vbproj. User или *имяПроекта*. csproj. User), и этот файл не находится в системе управления версиями. Если отладку выполняют сразу несколько пользователей, каждый из них вводит свойства отладки вручную.

 Если проект размещен в общей сетевой папке, а не в системе управления версиями, необходимо выполнить некоторые дополнительные действия, чтобы позволить разработчикам совместной работы открыть решение и протестировать сборку.

## <a name="source-control-requires-checking-out-all-files"></a>Система управления версиями требует извлечения всех файлов
 Если для проектов используется система управления версиями, следует извлекать все файлы в файле кода в **Обозреватель решений** (например, файлы кода *ThisDocument*, *ThisWorkbook* или *ThisAddIn* ) при каждом изменении файла кода, даже файлы, скрытые по умолчанию. Если вы извлекаете только файл кода верхнего уровня, изменения могут быть потеряны.

 После внесения изменений проверьте все файлы обратно. Дополнительные сведения о скрытых файлах кода в проектах см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Безопасность для неформальной совместной работы в сети
 Для всех решений на уровне документа, находящихся в сетевом расположении (например, \\ \\ *ServerName* \\ *ShareName*), полное расположение должно быть добавлено в список надежных папок в Microsoft Office приложении, с которым вы работаете. Выберите параметр для включения подкаталогов в основную папку или, в частности, добавьте папки отладки и сборки в список надежных папок. Дополнительные сведения о том, как это сделать, см. [в разделе Предоставление доверия документам](../vsto/granting-trust-to-documents.md).

 Временные сертификаты, автоматически формируемые во время сборки, не защищаются паролями. Сертификаты содержат имя входа разработчика и другие персональные данные. При развертывании настроек, подписанных временными сертификатами, другие пользователи могут получить доступ к этим сведениям.

## <a name="see-also"></a>См. также раздел
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Создание решений Office](../vsto/building-office-solutions.md)
