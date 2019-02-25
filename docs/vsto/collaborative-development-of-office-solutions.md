---
title: Совместная разработка решений Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 76c26a110d88d3dee8bf7540647ea0bfde4e7c4f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56635063"
---
# <a name="collaborative-development-of-office-solutions"></a>Совместная разработка решений Office
  Точно так же, они совместно работать над другими проектами Visual Studio в проекте Office могут работать несколько разработчиков. Visual Studio правильно определяет местоположение установки Microsoft Office на каждом компьютере, даже если Office устанавливается в разных расположениях. Однако существуют важные моменты, которые следует учитывать.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="debug-properties-are-not-shared"></a>Отладка свойств не являются общими
 Отладка свойств не выполняется для всех пользователей, зарегистрированных в системе контроля версий, одновременно. Visual Basic и Visual C# проекты сохраняют свойства отладки в файлы конкретных пользователей (*имя_проекта*. vbproj.user или *имя_проекта*. csproj.user), и этот файл не существует в системе управления версиями . Если отладку выполняют сразу несколько пользователей, каждый из них вводит свойства отладки вручную.

 Если проект расположен в сетевой папке, а не в системе управления версиями, некоторые дополнительные шаги необходимо выполнить для включения участникам совместной разработки откройте решение и протестируйте сборку.

## <a name="source-control-requires-checking-out-all-files"></a>Системы управления версиями требуется извлечение всех файлов
 Если вы используете систему управления версиями для проектов, стоит обратить внимание на все файлы в файл кода в **обозревателе решений** (такие как *ThisDocument*, *ThisWorkbook*, или *ThisAddIn* файлы кода) каждый раз при изменении файла кода, даже если файлы, которые скрыты по умолчанию. Если вы извлекаете только файл кода верхнего уровня, изменения будут утеряны.

 После внесения изменений, убедитесь, что все файлы обратно. Дополнительные сведения о скрытых файлах кода в проектах см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="security-for-informal-collaboration-on-a-network"></a>Безопасность для неформальной совместной работы в сети
 Для всех решений уровня документа, которые находятся в сети (таких как \\ \\ *Servername*\\*Sharename*), необходимо добавить полный путь к расположению в приложении Microsoft Office, которое вы работаете в список надежных папок. Выберите параметр для включения подкаталогов в главную папку или специально добавьте команду debug и создавать папки в список надежных папок. Дополнительные сведения о том, как это сделать, см. в разделе [предоставления доверия к документам](../vsto/granting-trust-to-documents.md).

 Временные сертификаты, которые создаются автоматически во время сборки не защищены с помощью паролей. Сертификаты содержат имя входа для разработчиков и другую личную информацию. При развертывании настроек, которые были подписаны временных сертификатов, другие же могут быть доступ к этой информации.

## <a name="see-also"></a>См. также
- [Безопасные решения Office](../vsto/securing-office-solutions.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)
- [Создание решений Office](../vsto/building-office-solutions.md)
