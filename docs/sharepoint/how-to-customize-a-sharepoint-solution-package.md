---
title: "Как: Настройка пакета решения SharePoint | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.SharePointTools.RAD.PackageDesignerAdvanced
- VS.SharePointTools.RAD.PackageDesigner.Manifest
- VS.SharePointTools.RAD.PackageDesignerProperties
- VS.SharePointTools.RAD.PackageDesigner.SwitchView
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packages
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 277ceea1b908c5819608a1bdf1d6be97c2f6ce77
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-customize-a-sharepoint-solution-package"></a>Практическое руководство. Настройка пакета решения SharePoint
  Конструктор пакетов можно использовать для создания и настройки пакета (.wsp). Например можно добавить элементы проектов SharePoint и компоненты, указать, если веб-сервер сброса при развертывании решения и задать тип сервера развертывания.  
  
## <a name="opening-the-package-designer"></a>Открытие конструктора пакетов  
  
#### <a name="to-open-the-package-designer"></a>Чтобы открыть конструктор пакетов  
  
-   В **обозревателе решений**, дважды щелкните **пакета**, или выберите **конструктор представлений** в контекстном меню для **пакета**.  
  
## <a name="viewing-the-packaged-manifest-file"></a>Просмотр файла манифеста в пакете  
 Конструктор пакетов можно использовать для изменения и создания файла манифеста в пакете. Затем можно просмотреть XML-код для этого файла в Visual Studio.  
  
#### <a name="to-view-the-xml-source-file"></a>Чтобы просмотреть исходный XML-файл  
  
1.  В **конструктора пакетов**, выберите **манифеста**.  
  
#### <a name="to-view-the-packaged-manifest-file-by-using-solution-explorer"></a>Чтобы просмотреть файл манифеста в пакете с помощью обозревателя решений  
  
1.  В **обозревателе решений**, выберите **Показать все файлы**.  
  
2.  Разверните пакет, разверните узел пакета и затем откройте файл Package.Template.xml.  
  
    > [!NOTE]  
    >  При открытии XML-файла манифеста шаблона пакета, автоматическая проверка файлов, и можно пропустить предупреждения, которые отображаются в окне списка ошибок.  
  
## <a name="changing-the-manifest-template"></a>Изменение шаблона манифеста  
 Можно изменить XML-код для файла манифеста в пакете в XML-редакторе Visual Studio или в шаблон манифеста области. Любые изменения кода XML, объединяются в файл манифеста пакета для пакета.  
  
#### <a name="to-change-the-manifest-template-by-using-the-xml-editor"></a>Изменение шаблона манифеста с помощью редактора XML  
  
1.  В **конструктора пакетов**, выберите **манифеста** , раскройте **Правка** узел и выберите **открыть в редакторе XML** ссылку.  
  
     Изменения в XML-документ, объединяются в файл манифеста в пакете.  
  
#### <a name="to-change-the-manifest-template-by-using-the-manifest-template-pane"></a>Изменение шаблона манифеста с помощью области шаблон манифеста  
  
1.  В **конструктора пакетов**, выберите **манифеста** , раскройте **Правка** узел, а затем измените XML, который появляется в области шаблон манифеста.  
  
     Изменения в XML-документ, отражаются в **Предварительный просмотр манифеста в пакете** области.  
  
## <a name="overwriting-the-packaged-manifest-file"></a>Перезапись файла манифеста в пакете  
 Можно отключить конструктор пакетов и создать файл manifest.xml вручную. Первый раз, при выполнении этой процедуры текущие параметры в конструкторе пакетов сохраняются в XML-файле шаблона пакета. Затем можно изменить или перезаписать XML-код.  
  
> [!NOTE]  
>  При добавлении или удалении компонентов и элементов проекта SharePoint в XML-файле при отключенном конструкторе пакетов эти компоненты и элементы проектов не пакет.  
  
#### <a name="to-overwrite-packaged-manifest-file-by-disabling-the-designer"></a>Чтобы перезаписать файл манифеста в пакете путем отключения конструктора  
  
1.  В **конструктора пакетов**, выберите **манифеста** вкладки.  
  
2.  .  
  
3.  Разверните **Правка** узел, выберите **Перезаписать созданный XML и редактировать манифест в редакторе XML** связь, а затем выберите **Да** кнопки.  
  
     Шаблон обновляется текущий файл манифеста в пакете.  
  
## <a name="enabling-the-package-designer"></a>Включение конструктора пакетов  
 Его можно снова включить конструктор пакетов для редактирования файла manifest.xml.  
  
#### <a name="to-re-enable-the-designer"></a>Чтобы снова включить конструктор  
  
1.  В **конструктора пакетов**, выберите **отменить изменения манифеста и включить конструктор** связь, а затем выберите **Да** кнопки.  
  
     Шаблон обновляется с исходным текстом и будут потеряны все изменения в XML-документ.  
  
## <a name="see-also"></a>См. также  
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  