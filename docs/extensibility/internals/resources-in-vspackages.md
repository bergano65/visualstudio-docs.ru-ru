---
title: Ресурсы в пакетах VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e058c55e96bed828223f021606a748b9da99254a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618930"
---
# <a name="resources-in-vspackages"></a>Ресурсы в пакетах VSPackage
Локализованные ресурсы можно внедрять в собственном спутниковой связи DLL пользовательского интерфейса и управляемых вспомогательных библиотек DLL, или в управляемом VSPackage сам.

 Некоторые ресурсы не может быть внедрен в пакетах VSPackage. Можно включить следующие управляемые типы:

- Строки

- Ключи загрузки пакетов (которые также являются строками)

- Значки окна средств

- Скомпилированные файлы таблицы выходных данных команды (CTO)

- Руководитель технологического ОТДЕЛА компании точечных рисунков

- Справка по командной строке

- О данных диалоговых окон

  Ресурсы в управляемом пакете выбираются по идентификатору ресурса. Исключением является файл руководитель технологического ОТДЕЛА компании, которая должна быть названа CTMENU. Файл руководитель технологического ОТДЕЛА компании должен указываться в нее ресурсов, как `byte[]`. Все прочие элементы ресурсов идентифицируются по типу.

  Можно использовать <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> атрибут для указания [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] что управляемые ресурсы доступны.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Установка <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> указывает, что таким образом [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] должен игнорировать неуправляемых вспомогательные библиотеки DLL, при поиске ресурсов, например, с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Если [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] обнаруживает два или более ресурсов, которые имеют тот же идентификатор ресурса, используется первый ресурс, он находит.

## <a name="example"></a>Пример
 Следующий пример — это управляемое представление значка окна инструментов.

```
<data name="1001"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyToolWinIcon.bmp;
     System.Drawing.Bitmap,
     System.Drawing,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

 Ниже приведен пример, как внедрять руководитель технологического ОТДЕЛА компании байтового массива, которая должна быть названа CTMENU.

```
<data name="CTMENU"
type="System.Resources.ResXFileRef,System.Windows.Forms">
     <value>
     MyPackage.cto;
     System.Byte[],
     mscorlib,
     Version=1.0.0.0,
     Culture=neutral,
     PublicKeyToken=b03f5f7f11d50a3a
     </value>
</data>
```

## <a name="implementation-notes"></a>Примечания по реализации
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] задержки загрузки пакетов VSPackage, когда это возможно. Следствием внедрения файл руководитель технологического ОТДЕЛА компании в VSPackage является то, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо загрузить всех таких пакетов VSPackage в памяти во время установки, при построении команды объединенные таблицы. Ресурсы могут быть извлечены из VSPackage с помощью проверки метаданных без выполнения кода в VSPackage. В настоящее время VSPackage не инициализирован, поэтому снижение производительности сводится к минимуму.

 Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запросы ресурс из VSPackage после завершения установки, он скорее всего, уже быть загружается и инициализируется, поэтому снижение производительности сводится к минимуму.

## <a name="see-also"></a>См. также
- [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)
- [Локализованные ресурсы в приложениях MFC: вспомогательные библиотеки DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
