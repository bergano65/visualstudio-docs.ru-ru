---
title: Решения по проектированию управления источниками (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], design decisions
ms.assetid: 5f60ec1a-5a74-4362-8293-817a4dd73872
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9c36bb2b50a72a52aeaeb7712f4ed711845b5e6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705245"
---
# <a name="source-control-design-decisions"></a>Проектные решения для системы управления версиями
При реализации управления исходным ресурсом следует учитывать следующие проектные решения для проектов.

## <a name="will-information-be-shared-or-private"></a>Будет ли информация передаваться или находиться в частной жизни?
 Наиболее важным проектным решением, который вы можете сделать, является то, что информация sharable и то, что является частным. Например, список файлов для проекта является общим, но в этом списке файлов некоторые пользователи могут захотеть иметь личные файлы. Настройки компилятора являются общими, но проект запуска, как правило, является закрытым. Настройки либо являются общими, общими с переопределением, либо чисто частными. По замыслу, частные элементы, такие как параметры решения [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](.suo) файлы, не проверяются в . Не забудьте хранить любую личную информацию в частных файлах, таких как файл .suo, или в специальном частном файле, который вы создаете, например, файл .csproj.user для Visual C или файл .vbproj.user для Visual Basic.

 Это решение не является всеобъемлющим и может быть принято на основе пункта по пункту.

## <a name="will-the-project-include-special-files"></a>Будет ли проект включать в себя специальные файлы?
 Другим важным проектным решением является использование структуры проекта специальными файлами. Специальные файлы — это скрытые файлы, лежащие в основе файлов, которые видны в Solution Explorer и в диалоговых коробках регистрации и регистрации. Если вы используете специальные файлы, следуйте следующим рекомендациям:

1. Не связывайте специальные файлы с корневым узлами проекта, то есть с самим файлом проекта. Файл проекта должен быть единым файлом.

2. При добавлении, удалении или переименовании <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> специальных файлов в проект соответствующие события должны быть уволены с набором флага, указывающим на то, что файлы являются специальными файлами. Эти события называются средой в ответ на <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> проект, называя соответствующие методы.

3. Когда ваш проект <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> или редактор вызывает файл, специальные файлы, связанные с этим файлом, автоматически не выдаются. Передайте специальные файлы вместе с родительским файлом. Среда будет обнаруживать связь между всеми файлами, которые передаются в и надлежащим образом скрыть специальные файлы в выездном uI.

## <a name="see-also"></a>См. также
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Поддержка системы управления версиями](../../extensibility/internals/supporting-source-control.md)
