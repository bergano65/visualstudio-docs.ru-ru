---
title: "Совместная разработка решений Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], collaborative development
- Office development in Visual Studio, collaboration
- source control [Office development in Visual Studio]
- collaborative development [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3b69eccc3f6c140c44bff3b2d3d24e33914cae84
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Совместная разработка решений Office
  Несколько дает разработчикам возможность работать в проекте Office таким же образом, они совместной работы на других проектов Visual Studio. Visual Studio правильно находит установки Microsoft Office на каждом компьютере, даже если Office устанавливается в разных местах. Однако существуют некоторые важные вопросы, которые следует учитывать.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Отладка свойств не выполняется  
 Отладка свойств не выполняется для всех пользователей, зарегистрированных в системе контроля версий, одновременно. Проекты Visual Basic и Visual C# сохраняют свойства отладки в файлы конкретных пользователей (*ProjectName*. vbproj.user или *ProjectName*. csproj.user), и этот файл не существует в системе управления версиями. Если отладку выполняют сразу несколько пользователей, каждый из них вводит свойства отладки вручную.  
  
 Если проект расположен на общем сетевом ресурсе, а не в системе управления версиями, чтобы разрешить участникам совместной разработки откройте решение и тестировать сборку необходимо выполнить некоторые дополнительные действия.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Система управления версиями требует извлечения всех файлов  
 Если используется система управления версиями для проектов, необходимо проверить все файлы в файл кода в **обозревателе решений** (например, файлы кода ThisAddIn, ThisWorkbook или ThisDocument) каждый раз при изменении файла кода, даже файлы, которые скрыты по умолчанию. Если вы извлекаете только файл кода верхнего уровня, внесенные изменения будут утеряны.  
  
 После внесения изменений, убедитесь, что все файлы обратно. Дополнительные сведения о скрытых файлах кода в проектах см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Безопасность для неформальной совместной работы в сети  
 Для всех решений уровня документа, которые находятся в сети (такие как \\ \\ *Servername*\\*Sharename*), необходимо добавить полный путь к расположению для в приложении Microsoft Office, которым вы работаете в список надежных папок. Выберите параметр для добавления подкаталогов основной папки или специально добавления отладки и построения папки в список надежных папок. Дополнительные сведения о том, как это сделать см. в разделе [Присвоение уровня доверия документам](../vsto/granting-trust-to-documents.md).  
  
 Временные сертификаты, которые были автоматически созданы во время сборки не защищены с помощью паролей. Сертификаты содержат имя входа для разработчиков и другие сведения личного характера. При развертывании настроек, подписанных временными сертификатами, другие могут быть доступ к этой информации.  
  
## <a name="see-also"></a>См. также  
 [Обеспечение безопасности решений Office](../vsto/securing-office-solutions.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Создание решений Office](../vsto/building-office-solutions.md)  
  
  