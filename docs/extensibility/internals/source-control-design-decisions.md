---
title: Источник проектные решения управления | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0385d5feb7baf7fe60e253616c8db0f326932e9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="source-control-design-decisions"></a>Исходный элемент управления проектных решений
При реализации системы управления версиями для проектов должны быть рассмотрены следующие конструктивные решения.  
  
## <a name="will-information-be-shared-or-private"></a>Сведения будут совместно используемой или закрытой?  
 Наиболее важные проектному решению, которые вы можете выполнить является какие сведения является общим, и каков закрытый. Например список файлов для проекта является общим, но в этот список файлов, некоторым пользователям может потребоваться личные файлы. Параметры компилятора используются совместно, но обычно закрытый запускаемого проекта. Параметры являются исключительно общего, общие с помощью переопределения или исключительно закрытый. Намеренно, личные элементы, такие как пользовательские решения параметры файлов (.suo) не возвращаются в [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]. Убедитесь, что для хранения конфиденциальных сведений в личные файлы, например SUO-файл или определенный файл закрытого создается, например,. csproj.user файл для Visual C# или. vbproj.user файл для Visual Basic.  
  
 Это решение не разрешены и могут выполняться на основе элементов.  
  
## <a name="will-the-project-include-special-files"></a>Будет ли проект включает специальные файлы?  
 Другое важное Проектное решение — ли структуры проекта используются специальные файлы. Специальные файлы, скрытые файлы, которые лежат в основе файлов, отображается в обозревателе решений и возврат и извлечение диалоговые окна. Если вы используете специальные файлы, придерживайтесь следующих правил:  
  
1.  Не связывайте специальные файлы с корневой узел проекта, то есть с проектом самом файле. Файл проекта должен быть один файл.  
  
2.  При Добавление, удаление или переименован в проекте, соответствующую специальные файлы <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> событий должен запускаться с установленным флагом, который указывает это специальные файлы. Эти события вызываются в ответ на вызов соответствующего проекта в среде <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> методы.  
  
3.  Если проект или редактор вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> для файла, специальные файлы, связанные с этим файлом не извлекаются автоматически. Передайте специальные файлы в родительском файле. Среде определяет связь между все файлы, которые передаются в и соответствующим образом скрыть специальные файлы, в пользовательском Интерфейсе извлечения.  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)