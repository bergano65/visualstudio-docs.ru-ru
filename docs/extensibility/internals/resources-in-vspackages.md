---
title: Ресурсы в пакетах VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, resources in
- resources, managed VSPackages
- VSPackages, managed resources
ms.assetid: cc8c17a6-b190-4856-b001-0c1104f104b2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07e1e19f802203b9770764330ea894b7d0eb98b8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724158"
---
# <a name="resources-in-vspackages"></a>Ресурсы в пакетах VSPackage
Локализованные ресурсы можно внедрять в встроенные библиотеки DLL пользовательского интерфейса, управляемые вспомогательные библиотеки DLL или в самом управляемом пакете VSPackage.

 Некоторые ресурсы не могут быть внедрены в пакеты VSPackage. Можно внедрить следующие управляемые типы:

- Строки

- Ключи загрузки пакета (которые также являются строками)

- Значки окна инструментов

- Скомпилированные файлы вывода командной таблицы (CTO)

- Точечные рисунки CTO

- Справка по командной строке

- О данных диалоговых окон

  Ресурсы в управляемом пакете выбираются по ИДЕНТИФИКАТОРу ресурса. Исключением является файл CTO, который должен иметь имя CTMENU. Файл CTO должен отображаться в таблице ресурсов как `byte[]`. Все остальные элементы ресурсов идентифицируются по типу.

  Можно использовать атрибут <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, чтобы указать [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], что управляемые ресурсы доступны.

  [!code-csharp[VSSDKResources#1](../../extensibility/internals/codesnippet/CSharp/resources-in-vspackages_1.cs)]
  [!code-vb[VSSDKResources#1](../../extensibility/internals/codesnippet/VisualBasic/resources-in-vspackages_1.vb)]

  Установка <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> таким образом означает, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] должны игнорировать неуправляемые вспомогательные библиотеки DLL при поиске ресурсов, например с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackageString%2A>. Если [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] встречает два или больше ресурсов с одинаковым ИДЕНТИФИКАТОРом ресурса, он использует первый найденный ресурс.

## <a name="example"></a>Пример
 В следующем примере представлено управляемое представление значка окна инструментов.

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

 В следующем примере показано, как внедрить массив байтов CTO, который должен иметь имя CTMENU.

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
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] задерживает загрузку пакетов VSPackage везде, где это возможно. Следствием внедрения файла CTO в VSPackage является то, что [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] должны загружать все такие пакеты VSPackage в памяти во время установки, то есть при построении Объединенной командной таблицы. Ресурсы можно извлечь из пакета VSPackage, проверив метаданные без выполнения кода в VSPackage. В настоящее время пакет VSPackage не инициализирован, поэтому снижение производительности является минимальным.

 Когда [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] запрашивает ресурс из пакета VSPackage после установки, этот пакет, скорее всего, уже загружен и инициализирован, поэтому снижение производительности является минимальным.

## <a name="see-also"></a>См. также
- [Управление пакетами VSPackage](../../extensibility/managing-vspackages.md)
- [Локализованные ресурсы в приложениях MFC: вспомогательные библиотеки DLL](/cpp/build/localized-resources-in-mfc-applications-satellite-dlls)
