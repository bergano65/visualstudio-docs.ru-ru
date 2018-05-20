---
title: Совместная разработка решений Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9bf85dd1ba39df35e337f1b6b80099e3d5bcd774
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="collaborative-development-of-office-solutions"></a>Совместная разработка решений Office
  Несколько дает разработчикам возможность работать в проекте Office таким же образом, они совместной работы на других проектов Visual Studio. Visual Studio правильно находит установки Microsoft Office на каждом компьютере, даже если Office устанавливается в разных местах. Однако существуют некоторые важные вопросы, которые следует учитывать.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="debug-properties-are-not-shared"></a>Отладка свойств не выполняется  
 Отладка свойств не выполняется для всех пользователей, зарегистрированных в системе контроля версий, одновременно. Проекты Visual Basic и Visual C# сохраняют свойства отладки в файлы конкретных пользователей (*ProjectName*. vbproj.user или *ProjectName*. csproj.user), и этот файл не существует в системе управления версиями. Если отладку выполняют сразу несколько пользователей, каждый из них вводит свойства отладки вручную.  
  
 Если проект расположен на общем сетевом ресурсе, а не в системе управления версиями, чтобы разрешить участникам совместной разработки откройте решение и тестировать сборку необходимо выполнить некоторые дополнительные действия.  
  
## <a name="source-control-requires-checking-out-all-files"></a>Система управления версиями требует извлечения всех файлов  
 Если используется система управления версиями для проектов, необходимо проверить все файлы в файл кода в **обозревателе решений** (такие как *ThisDocument*, *ThisWorkbook*, или *ThisAddIn* файлов с текстом) каждый раз при изменении файла кода, даже если файлы по умолчанию скрыты. Если вы извлекаете только файл кода верхнего уровня, внесенные изменения будут утеряны.  
  
 После внесения изменений, убедитесь, что все файлы обратно. Дополнительные сведения о скрытых файлах кода в проектах см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="security-for-informal-collaboration-on-a-network"></a>Безопасность для неформальной совместной работы в сети  
 Для всех решений уровня документа, которые находятся в сети (такие как \\ \\ *Servername*\\*Sharename*), необходимо добавить полный путь к расположению для в приложении Microsoft Office, которым вы работаете в список надежных папок. Выберите параметр для добавления подкаталогов основной папки или специально добавления отладки и построения папки в список надежных папок. Дополнительные сведения о том, как это сделать см. в разделе [предоставить доверие к документам](../vsto/granting-trust-to-documents.md).  
  
 Временные сертификаты, которые были автоматически созданы во время сборки не защищены с помощью паролей. Сертификаты содержат имя входа для разработчиков и другие сведения личного характера. При развертывании настроек, подписанных временными сертификатами, другие могут быть доступ к этой информации.  
  
## <a name="see-also"></a>См. также  
 [Безопасные решения Office](../vsto/securing-office-solutions.md)   
 [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md)   
 [Создание решений Office](../vsto/building-office-solutions.md)  
  
  