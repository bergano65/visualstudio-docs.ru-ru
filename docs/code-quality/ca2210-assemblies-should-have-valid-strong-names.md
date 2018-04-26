---
title: 'CA2210: сборки должны иметь допустимые строгие имена'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b7fb5f55ee345fa47a4a4510fe8121b82d1c0ae
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: сборки должны иметь допустимые строгие имена
|||
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|Категория|Microsoft.Design|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Сборка не подписана строгим именем, не удалось проверить строгое имя или строгое имя, будет недействителен без текущих параметров реестра компьютера.

## <a name="rule-description"></a>Описание правила
 Это правило получает и проверяет строгое имя сборки. Нарушение возникает, если хотя бы одно из следующих:

-   Сборка не имеет строгого имени.

-   Сборка была изменена после подписания.

-   Сборка является отложенной подписью.

-   Сборка была подписана неверно или не удалось подписать.

-   Сборку требуется настроить параметры реестра для проверки. Например средство строгих имен (Sn.exe) была использована для пропуска проверки для сборки.

 Строгое имя защищает клиентов от случайной загрузки сборки, которая была подменена. Сборки без строгих имен следует развертывать лишь в крайне небольшом числе случаев. При обмене или распространении сборок без правильной подписи сборки могут быть подменены, среда CLR может не загрузить сборку или пользователь может быть вынужден отключить проверку на своем компьютере. Сборки без строгого имени имеет следующие недостатки:

-   Не удается проверить ее происхождение.

-   Общеязыковая среда выполнения не может предупредить пользователей, если содержимое сборки было изменено.

-   Не удается загрузить в глобальный кэш сборок.

 Обратите внимание, что для загрузки и анализа сборки с отложенной подписью, необходимо отключить проверку сборки.

## <a name="how-to-fix-violations"></a>Устранение нарушений
 **Чтобы создать файл ключа**

 Используйте один из следующих процедур:

-   Используйте средство компоновщик сборок (Al.exe), предоставляемого [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK.

-   Для [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] v1.0 или v1.1, используйте либо <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> или <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> атрибута.

-   Для [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], либо использовать `/keyfile` или `/keycontainer` параметр компилятора [/keyfile (указать ключ или пары ключей для подписи сборки)](/cpp/build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly) или  [ /keycontainer (указание контейнера ключей для подписи сборки)](/cpp/build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly) параметра компоновщика в C++).

 **Чтобы подписать сборку строгим именем в Visual Studio**

1.  В [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], откройте решение.

2.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **свойства.**

3.  Нажмите кнопку **подписывание** и выберите **подписать сборку** флажок.

4.  Из **выберите файл ключей строгого имени**выберите **New**.

     **Создание ключа строгого имени** окне будут отображаться.

5.  В **имя файла ключа**, введите имя для своего ключа строгого имени.

6.  Выберите, следует ли защитить ключ паролем и нажмите кнопку **ОК**.

7.  В **обозревателе решений**, щелкните правой кнопкой мыши проект и нажмите кнопку **сборки**.

 **Чтобы подписать сборку строгим именем вне Visual Studio**

-   Используйте средство строгих имен (Sn.exe), предоставляемый [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] SDK. Дополнительные сведения см. на странице [Sn.exe (Strong Name Tool)](/dotnet/framework/tools/sn-exe-strong-name-tool) (Sn.exe: средство строгих имен).

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Только отключайте предупреждение из этого правила, если сборка используется в среде, где подмена содержимого не имеет значения.

## <a name="see-also"></a>См. также
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> [Как: подписать сборку строгим именем](/dotnet/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name) [Sn.exe (средство строгих имен)](/dotnet/framework/tools/sn-exe-strong-name-tool)