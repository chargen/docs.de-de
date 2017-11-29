---
title: F#-Typen
description: "Erfahren Sie, bis die Typen, die verwendet werden, in F# erläutert werden und wie f#-Typen mit dem Namen beschrieben werden."
keywords: Visual F#, F#, funktionale Programmierung
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c7272a0d-5ab6-4eae-bceb-e49af498b917
ms.openlocfilehash: 9b7235637f301f91ae2cc8fbc59adc27cdfd5bd0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2017
---
# <a name="f-types"></a><span data-ttu-id="df000-104">F#-Typen</span><span class="sxs-lookup"><span data-stu-id="df000-104">F# Types</span></span>

<span data-ttu-id="df000-105">Dieses Thema beschreibt die Typen, die verwendet werden, in F# erläutert werden und wie f#-Typen mit dem Namen beschrieben werden.</span><span class="sxs-lookup"><span data-stu-id="df000-105">This topic describes the types that are used in F# and how F# types are named and described.</span></span>


## <a name="summary-of-f-types"></a><span data-ttu-id="df000-106">Zusammenfassung der f#-Typen</span><span class="sxs-lookup"><span data-stu-id="df000-106">Summary of F# Types</span></span>
<span data-ttu-id="df000-107">Einige Typen gelten als *Grundtypen*, z. B. boolescher Typ `bool` und Ganzzahl- und Gleitkommatyps Verbindungspunkttypen mit verschiedenen Größen, die Typen für Bytes und Zeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="df000-107">Some types are considered *primitive types*, such as the Boolean type `bool` and integral and floating point types of various sizes, which include types for bytes and characters.</span></span> <span data-ttu-id="df000-108">Diese Typen werden in beschrieben [Grundtypen](primitive-types.md).</span><span class="sxs-lookup"><span data-stu-id="df000-108">These types are described in [Primitive Types](primitive-types.md).</span></span>

<span data-ttu-id="df000-109">Andere Typen, die in der Sprache integrierte einschließen, Tupeln, Listen, Arrays, Sequenzen, Datensätze und Unterscheidungs-Unions.</span><span class="sxs-lookup"><span data-stu-id="df000-109">Other types that are built into the language include tuples, lists, arrays, sequences, records, and discriminated unions.</span></span> <span data-ttu-id="df000-110">Wenn Sie verfügen über Erfahrung mit anderen .NET-Sprachen und lernen f# sind, sollten Sie für jeden dieser Typen in den Themen lesen.</span><span class="sxs-lookup"><span data-stu-id="df000-110">If you have experience with other .NET languages and are learning F#, you should read the topics for each of these types.</span></span> <span data-ttu-id="df000-111">Links zu weiteren Informationen über diese Typen befinden sich die [Verwandte Themen](https://msdn.microsoft.com/library/#rel) Abschnitt dieses Themas.</span><span class="sxs-lookup"><span data-stu-id="df000-111">Links to more information about these types are included in the [Related Topics](https://msdn.microsoft.com/library/#rel) section of this topic.</span></span> <span data-ttu-id="df000-112">Die f#-Unterstützung für bestimmte Programmierstile, die für die funktionalen Programmiersprachen gelten.</span><span class="sxs-lookup"><span data-stu-id="df000-112">These F#-specific types support styles of programming that are common to functional programming languages.</span></span> <span data-ttu-id="df000-113">Viele dieser Typen sind Module in der F#-Bibliothek zugeordnet, die häufig verwendeter Vorgänge auf diese Typen zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="df000-113">Many of these types have associated modules in the F# library that support common operations on these types.</span></span>

<span data-ttu-id="df000-114">Der Typ einer Funktion enthält Informationen zu den Parametertypen und Rückgabetyp.</span><span class="sxs-lookup"><span data-stu-id="df000-114">The type of a function includes information about the parameter types and return type.</span></span>

<span data-ttu-id="df000-115">.NET Framework ist die Quelle von Objekttypen, Schnittstellentypen und Delegattypen.</span><span class="sxs-lookup"><span data-stu-id="df000-115">The .NET Framework is the source of object types, interface types, delegate types, and others.</span></span> <span data-ttu-id="df000-116">Sie können eigene Objekttypen definieren, ebenso wie Sie in jeder anderen.</span><span class="sxs-lookup"><span data-stu-id="df000-116">You can define your own object types just as you can in any other .NET language.</span></span>

<span data-ttu-id="df000-117">F#-Code kann auch mit dem Namen sind Aliase definieren *typabkürzungen*, alternative Namen für Typen sind.</span><span class="sxs-lookup"><span data-stu-id="df000-117">Also, F# code can define aliases, which are named *type abbreviations*, that are alternative names for types.</span></span> <span data-ttu-id="df000-118">Sie können typabkürzungen verwenden, wenn der Typ in der Zukunft ändern kann und Sie möchten, um zu vermeiden, ändern den Code, der hängt vom Typ.</span><span class="sxs-lookup"><span data-stu-id="df000-118">You might use type abbreviations when the type might change in the future and you want to avoid changing the code that depends on the type.</span></span> <span data-ttu-id="df000-119">Oder Sie typabkürzung als einen Anzeigenamen für einen Typ, der Code leichter kann lesbar und verständlicher zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="df000-119">Or, you might use a type abbreviation as a friendly name for a type that can make code easier to read and understand.</span></span>

<span data-ttu-id="df000-120">F# bietet nützliche Auflistungstypen, die mit der funktionalen Programmierung Bedenken vorgesehen sind.</span><span class="sxs-lookup"><span data-stu-id="df000-120">F# provides useful collection types that are designed with functional programming in mind.</span></span> <span data-ttu-id="df000-121">Verwenden diese Auflistungstypen können Sie Code schreiben, die im Format mehr funktionsfähig ist.</span><span class="sxs-lookup"><span data-stu-id="df000-121">Using these collection types helps you write code that is more functional in style.</span></span> <span data-ttu-id="df000-122">Weitere Informationen finden Sie unter [f#-Auflistungstypen](fsharp-collection-types.md).</span><span class="sxs-lookup"><span data-stu-id="df000-122">For more information, see [F# Collection Types](fsharp-collection-types.md).</span></span>


## <a name="syntax-for-types"></a><span data-ttu-id="df000-123">Syntax für Typen</span><span class="sxs-lookup"><span data-stu-id="df000-123">Syntax for Types</span></span>
<span data-ttu-id="df000-124">In f#-Code müssen Sie häufig die Namen von Typen zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="df000-124">In F# code, you often have to write out the names of types.</span></span> <span data-ttu-id="df000-125">Jeder Typ weist einen Syntaxform, und Sie verwenden diese syntaktischen Formen in abstrakten Methodendeklarationen, typanmerkungen, Delegatdeklarationen, Signaturen und andere Konstrukte.</span><span class="sxs-lookup"><span data-stu-id="df000-125">Every type has a syntactic form, and you use these syntactic forms in type annotations, abstract method declarations, delegate declarations, signatures, and other constructs.</span></span> <span data-ttu-id="df000-126">Wenn Sie ein neues Programmkonstrukt in den Interpreter deklarieren, gibt der Interpreter den Namen des Konstrukts und die Syntax für seinen Typ.</span><span class="sxs-lookup"><span data-stu-id="df000-126">Whenever you declare a new program construct in the interpreter, the interpreter prints the name of the construct and the syntax for its type.</span></span> <span data-ttu-id="df000-127">Diese Syntax ist möglicherweise nur ein Bezeichner für einen benutzerdefinierten Typ oder ein integrierter Bezeichner, z. B. für `int` oder `string`, jedoch ist die Syntax für komplexere Typen komplexer.</span><span class="sxs-lookup"><span data-stu-id="df000-127">This syntax might be just an identifier for a user-defined type or a built-in identifier such as for `int` or `string`, but for more complex types, the syntax is more complex.</span></span>

<span data-ttu-id="df000-128">Die folgende Tabelle zeigt die Aspekte der Type-Syntax für f#-Typen.</span><span class="sxs-lookup"><span data-stu-id="df000-128">The following table shows aspects of the type syntax for F# types.</span></span>



|<span data-ttu-id="df000-129">Typ</span><span class="sxs-lookup"><span data-stu-id="df000-129">Type</span></span>|<span data-ttu-id="df000-130">Type-syntax</span><span class="sxs-lookup"><span data-stu-id="df000-130">Type syntax</span></span>|<span data-ttu-id="df000-131">Beispiele</span><span class="sxs-lookup"><span data-stu-id="df000-131">Examples</span></span>|
|----|-----------|--------|
|<span data-ttu-id="df000-132">Grundtyp</span><span class="sxs-lookup"><span data-stu-id="df000-132">primitive type</span></span>|<span data-ttu-id="df000-133">*Typname*</span><span class="sxs-lookup"><span data-stu-id="df000-133">*type-name*</span></span>|`int`<br /><br />`float`<br /><br />`string`|
|<span data-ttu-id="df000-134">aggregierten Typs (Klasse, Struktur, Union, Datensatz, Enum, usw.)</span><span class="sxs-lookup"><span data-stu-id="df000-134">aggregate type (class, structure, union, record, enum, and so on)</span></span>|<span data-ttu-id="df000-135">*Typname*</span><span class="sxs-lookup"><span data-stu-id="df000-135">*type-name*</span></span>|`System.DateTime`<br /><br />`Color`|
|<span data-ttu-id="df000-136">-typabkürzung</span><span class="sxs-lookup"><span data-stu-id="df000-136">type abbreviation</span></span>|<span data-ttu-id="df000-137">*Abkürzung Typnamen*</span><span class="sxs-lookup"><span data-stu-id="df000-137">*type-abbreviation-name*</span></span>|`bigint`|
|<span data-ttu-id="df000-138">vollqualifizierte Typ</span><span class="sxs-lookup"><span data-stu-id="df000-138">fully qualified type</span></span>|<span data-ttu-id="df000-139">*Namespaces.Type-name*</span><span class="sxs-lookup"><span data-stu-id="df000-139">*namespaces.type-name*</span></span><br /><br /><span data-ttu-id="df000-140">oder</span><span class="sxs-lookup"><span data-stu-id="df000-140">or</span></span><br /><br /><span data-ttu-id="df000-141">*Modules.Type-name*</span><span class="sxs-lookup"><span data-stu-id="df000-141">*modules.type-name*</span></span><br /><br /><span data-ttu-id="df000-142">oder</span><span class="sxs-lookup"><span data-stu-id="df000-142">or</span></span><br /><br /><span data-ttu-id="df000-143">*Namespaces.Modules.Type-name*</span><span class="sxs-lookup"><span data-stu-id="df000-143">*namespaces.modules.type-name*</span></span>|`System.IO.StreamWriter`|
|<span data-ttu-id="df000-144">array</span><span class="sxs-lookup"><span data-stu-id="df000-144">array</span></span>|<span data-ttu-id="df000-145">*Typname*[] oder</span><span class="sxs-lookup"><span data-stu-id="df000-145">*type-name*[] or</span></span><br /><br /><span data-ttu-id="df000-146">*Typname* Array</span><span class="sxs-lookup"><span data-stu-id="df000-146">*type-name* array</span></span>|`int[]`<br /><br />`array<int>`<br /><br />`int array`|
|<span data-ttu-id="df000-147">zweidimensionales array</span><span class="sxs-lookup"><span data-stu-id="df000-147">two-dimensional array</span></span>|<span data-ttu-id="df000-148">*Typname*[,]</span><span class="sxs-lookup"><span data-stu-id="df000-148">*type-name*[,]</span></span>|`int[,]`<br /><br />`float[,]`|
|<span data-ttu-id="df000-149">dreidimensionale array</span><span class="sxs-lookup"><span data-stu-id="df000-149">three-dimensional array</span></span>|<span data-ttu-id="df000-150">*Typname*[,]</span><span class="sxs-lookup"><span data-stu-id="df000-150">*type-name*[,,]</span></span>|`float[,,]`|
|<span data-ttu-id="df000-151">tuple</span><span class="sxs-lookup"><span data-stu-id="df000-151">tuple</span></span>|<span data-ttu-id="df000-152">*Typ-name1* &#42; *Typ name2* ...</span><span class="sxs-lookup"><span data-stu-id="df000-152">*type-name1* &#42; *type-name2* ...</span></span>|<span data-ttu-id="df000-153">Beispielsweise `(1,'b',3)` weist den Typ`int * char * int`</span><span class="sxs-lookup"><span data-stu-id="df000-153">For example, `(1,'b',3)` has type `int * char * int`</span></span>|
|<span data-ttu-id="df000-154">generischer Typ</span><span class="sxs-lookup"><span data-stu-id="df000-154">generic type</span></span>|<span data-ttu-id="df000-155">*Typparameter* *generische-Type-Name*</span><span class="sxs-lookup"><span data-stu-id="df000-155">*type-parameter* *generic-type-name*</span></span><br /><br /><span data-ttu-id="df000-156">oder</span><span class="sxs-lookup"><span data-stu-id="df000-156">or</span></span><br /><br /><span data-ttu-id="df000-157">*generische Typnamen*&lt;*Typparameterliste*&gt;</span><span class="sxs-lookup"><span data-stu-id="df000-157">*generic-type-name*&lt;*type-parameter-list*&gt;</span></span>|`'a list`<br /><br />`list<'a>`<br /><br />`Dictionary<'key, 'value>`|
|<span data-ttu-id="df000-158">konstruierter Typ (ein generischer Typ, die ein bestimmten angegebene Typargument aufweist)</span><span class="sxs-lookup"><span data-stu-id="df000-158">constructed type (a generic type that has a specific type argument supplied)</span></span>|<span data-ttu-id="df000-159">*Argument vom Typ* *generische-Type-Name*</span><span class="sxs-lookup"><span data-stu-id="df000-159">*type-argument* *generic-type-name*</span></span><br /><br /><span data-ttu-id="df000-160">oder</span><span class="sxs-lookup"><span data-stu-id="df000-160">or</span></span><br /><br /><span data-ttu-id="df000-161">*generische Typnamen*&lt;*Typargumentliste*&gt;</span><span class="sxs-lookup"><span data-stu-id="df000-161">*generic-type-name*&lt;*type-argument-list*&gt;</span></span>|`int option`<br /><br />`string list`<br /><br />`int ref`<br /><br />`option<int>`<br /><br />`list<string>`<br /><br />`ref<int>`<br /><br />`Dictionary<int, string>`|
|<span data-ttu-id="df000-162">Typ der Funktion, die einen einzelnen Parameter verfügt.</span><span class="sxs-lookup"><span data-stu-id="df000-162">function type that has a single parameter</span></span>|<span data-ttu-id="df000-163">*Parameter-Typ1*  - &gt; *Return-Type*</span><span class="sxs-lookup"><span data-stu-id="df000-163">*parameter-type1* -&gt; *return-type*</span></span>|<span data-ttu-id="df000-164">Eine Funktion, übernimmt ein `int` und gibt eine `string` weist den Typ`int -> string`</span><span class="sxs-lookup"><span data-stu-id="df000-164">A function that takes an `int` and returns a `string` has type `int -> string`</span></span>|
|<span data-ttu-id="df000-165">Funktionstyp, der mehrere Parameter verfügt</span><span class="sxs-lookup"><span data-stu-id="df000-165">function type that has multiple parameters</span></span>|<span data-ttu-id="df000-166">*Parameter-Typ1*  - &gt; *Parameter Typ2*  - &gt; ... -&gt; *Return-Type*</span><span class="sxs-lookup"><span data-stu-id="df000-166">*parameter-type1* -&gt; *parameter-type2* -&gt; ... -&gt; *return-type*</span></span>|<span data-ttu-id="df000-167">Eine Funktion, übernimmt ein `int` und ein `float` und gibt eine `string` weist den Typ`int -> float -> string`</span><span class="sxs-lookup"><span data-stu-id="df000-167">A function that takes an `int` and a `float` and returns a `string` has type `int -> float -> string`</span></span>|
|<span data-ttu-id="df000-168">Funktion höherer Ordnung als parameter</span><span class="sxs-lookup"><span data-stu-id="df000-168">higher order function as a parameter</span></span>|<span data-ttu-id="df000-169">(*Funktionstyp*)</span><span class="sxs-lookup"><span data-stu-id="df000-169">(*function-type*)</span></span>|<span data-ttu-id="df000-170">`List.map`weist den Typ`('a -> 'b) -> 'a list -> 'b list`</span><span class="sxs-lookup"><span data-stu-id="df000-170">`List.map` has type `('a -> 'b) -> 'a list -> 'b list`</span></span>|
|<span data-ttu-id="df000-171">delegate</span><span class="sxs-lookup"><span data-stu-id="df000-171">delegate</span></span>|<span data-ttu-id="df000-172">Delegieren von *Funktionstyp*</span><span class="sxs-lookup"><span data-stu-id="df000-172">delegate of *function-type*</span></span>|`delegate of unit -> int`|
|<span data-ttu-id="df000-173">Flexible Typ</span><span class="sxs-lookup"><span data-stu-id="df000-173">flexible type</span></span>|<span data-ttu-id="df000-174">#*Typname*</span><span class="sxs-lookup"><span data-stu-id="df000-174">#*type-name*</span></span>|`#System.Windows.Forms.Control`<br /><br />`#seq<int>`|

## <a name="related-topics"></a><span data-ttu-id="df000-175">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="df000-175">Related Topics</span></span>


|<span data-ttu-id="df000-176">Thema</span><span class="sxs-lookup"><span data-stu-id="df000-176">Topic</span></span>|<span data-ttu-id="df000-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="df000-177">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="df000-178">Primitive Typen</span><span class="sxs-lookup"><span data-stu-id="df000-178">Primitive Types</span></span>](primitive-types.md)|<span data-ttu-id="df000-179">Beschreibt, wie z. B. ganzzahligen Typen, Boolean-Typ und Zeichentypen integrierte einfache Typen.</span><span class="sxs-lookup"><span data-stu-id="df000-179">Describes built-in simple types such as integral types, the Boolean type, and character types.</span></span>|
|[<span data-ttu-id="df000-180">Unit-Typ</span><span class="sxs-lookup"><span data-stu-id="df000-180">Unit Type</span></span>](unit-type.md)|<span data-ttu-id="df000-181">Beschreibt die `unit` Typ, ein Typ, der einen Wert aufweist, und () angegeben wird, entspricht der `void` in C# geschrieben und `Nothing` in Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="df000-181">Describes the `unit` type, a type that has one value and that is indicated by (); equivalent to `void` in C# and `Nothing` in Visual Basic.</span></span>|
|[<span data-ttu-id="df000-182">Tupel</span><span class="sxs-lookup"><span data-stu-id="df000-182">Tuples</span></span>](tuples.md)|<span data-ttu-id="df000-183">Beschreibt den Tupeltyp, einen Typ, der zugehörigen Werte eines beliebigen Typs gruppiert in Paare, Tripel, Quadrupel usw. besteht.</span><span class="sxs-lookup"><span data-stu-id="df000-183">Describes the tuple type, a type that consists of associated values of any type grouped in pairs, triples, quadruples, and so on.</span></span>|
|[<span data-ttu-id="df000-184">Optionen</span><span class="sxs-lookup"><span data-stu-id="df000-184">Options</span></span>](options.md)|<span data-ttu-id="df000-185">Beschreibt den Optionstyp, ein Typ, der möglicherweise entweder einen Wert oder leer sein.</span><span class="sxs-lookup"><span data-stu-id="df000-185">Describes the option type, a type that may either have a value or be empty.</span></span>|
|[<span data-ttu-id="df000-186">Listen</span><span class="sxs-lookup"><span data-stu-id="df000-186">Lists</span></span>](lists.md)|<span data-ttu-id="df000-187">Beschreibt, Listen, die geordnete, unveränderliche Reihe von Elementen werden alle den gleichen Typ aufweisen.</span><span class="sxs-lookup"><span data-stu-id="df000-187">Describes lists, which are ordered, immutable series of elements all of the same type.</span></span>|
|[<span data-ttu-id="df000-188">Arrays</span><span class="sxs-lookup"><span data-stu-id="df000-188">Arrays</span></span>](arrays.md)|<span data-ttu-id="df000-189">Beschreibt Arrays, die Sätze von änderbare-Elementen des gleichen Typs sortiert werden, die einen zusammenhängenden Block von Arbeitsspeicher belegen und haben eine feste Größe.</span><span class="sxs-lookup"><span data-stu-id="df000-189">Describes arrays, which are ordered sets of mutable elements of the same type that occupy a contiguous block of memory and are of fixed size.</span></span>|
|[<span data-ttu-id="df000-190">Sequenzen</span><span class="sxs-lookup"><span data-stu-id="df000-190">Sequences</span></span>](sequences.md)|<span data-ttu-id="df000-191">Beschreibt die Sequence-Typs, die eine logische Reihe von Werten darstellt. einzelne Werte werden nur nach Bedarf berechnet.</span><span class="sxs-lookup"><span data-stu-id="df000-191">Describes the sequence type, which represents a logical series of values; individual values are computed only as necessary.</span></span>|
|[<span data-ttu-id="df000-192">Datensätze</span><span class="sxs-lookup"><span data-stu-id="df000-192">Records</span></span>](records.md)|<span data-ttu-id="df000-193">Beschreibt den Datensatztyp, ein kleines Aggregat benannter Werte an.</span><span class="sxs-lookup"><span data-stu-id="df000-193">Describes the record type, a small aggregate of named values.</span></span>|
|[<span data-ttu-id="df000-194">Unterscheidbare Unions</span><span class="sxs-lookup"><span data-stu-id="df000-194">Discriminated Unions</span></span>](discriminated-unions.md)|<span data-ttu-id="df000-195">Beschreibt den diskriminierten union-Typ, ein Typ, dessen Werte eines eine Gruppe möglicher Typen sein können.</span><span class="sxs-lookup"><span data-stu-id="df000-195">Describes the discriminated union type, a type whose values can be any one of a set of possible types.</span></span>|
|[<span data-ttu-id="df000-196">Funktionen</span><span class="sxs-lookup"><span data-stu-id="df000-196">Functions</span></span>](functions/index.md)|<span data-ttu-id="df000-197">Beschreibt Funktionswerte an.</span><span class="sxs-lookup"><span data-stu-id="df000-197">Describes function values.</span></span>|
|[<span data-ttu-id="df000-198">Klassen</span><span class="sxs-lookup"><span data-stu-id="df000-198">Classes</span></span>](classes.md)|<span data-ttu-id="df000-199">Beschreibt den Klassentyp, ein Objekttyp, der ein Verweistyp .NET entspricht.</span><span class="sxs-lookup"><span data-stu-id="df000-199">Describes the class type, an object type that corresponds to a .NET reference type.</span></span> <span data-ttu-id="df000-200">Klassentypen können Member, Eigenschaften, implementierten Schnittstellen und ein Basistyp enthalten.</span><span class="sxs-lookup"><span data-stu-id="df000-200">Class types can contain members, properties, implemented interfaces, and a base type.</span></span>|
|[<span data-ttu-id="df000-201">Strukturen</span><span class="sxs-lookup"><span data-stu-id="df000-201">Structures</span></span>](structures.md)|<span data-ttu-id="df000-202">Beschreibt die `struct` Typ, ein Objekttyp, der einen Werttyp .NET entspricht.</span><span class="sxs-lookup"><span data-stu-id="df000-202">Describes the `struct` type, an object type that corresponds to a .NET value type.</span></span> <span data-ttu-id="df000-203">Die `struct` Typ in der Regel ein kleines Aggregat von Daten darstellt.</span><span class="sxs-lookup"><span data-stu-id="df000-203">The `struct` type usually represents a small aggregate of data.</span></span>|
|[<span data-ttu-id="df000-204">Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="df000-204">Interfaces</span></span>](interfaces.md)|<span data-ttu-id="df000-205">Beschreibt, Schnittstellentypen, Typen, die eine Menge von Elementen darstellen, die bestimmte Funktionen bereitstellen, aber keine Daten enthalten.</span><span class="sxs-lookup"><span data-stu-id="df000-205">Describes interface types, which are types that represent a set of members that provide certain functionality but that contain no data.</span></span> <span data-ttu-id="df000-206">Ein Schnittstellentyp muss durch einen Objekttyp, aussagekräftige implementiert werden.</span><span class="sxs-lookup"><span data-stu-id="df000-206">An interface type must be implemented by an object type to be useful.</span></span>|
|[<span data-ttu-id="df000-207">Delegaten</span><span class="sxs-lookup"><span data-stu-id="df000-207">Delegates</span></span>](delegates.md)|<span data-ttu-id="df000-208">Beschreibt den Delegattyp, der eine Funktion als ein Objekt darstellt.</span><span class="sxs-lookup"><span data-stu-id="df000-208">Describes the delegate type, which represents a function as an object.</span></span>|
|[<span data-ttu-id="df000-209">Enumerationen</span><span class="sxs-lookup"><span data-stu-id="df000-209">Enumerations</span></span>](enumerations.md)|<span data-ttu-id="df000-210">Beschreibt, Enumerationstypen,, deren Werte auf einen Satz benannter Werte gehören.</span><span class="sxs-lookup"><span data-stu-id="df000-210">Describes enumeration types, whose values belong to a set of named values.</span></span>|
|[<span data-ttu-id="df000-211">Attribute</span><span class="sxs-lookup"><span data-stu-id="df000-211">Attributes</span></span>](attributes.md)|<span data-ttu-id="df000-212">Beschreibt die Attribute, die verwendet werden, um Metadaten für einen anderen Typ angeben.</span><span class="sxs-lookup"><span data-stu-id="df000-212">Describes attributes, which are used to specify metadata for another type.</span></span>|
|[<span data-ttu-id="df000-213">Ausnahmetypen</span><span class="sxs-lookup"><span data-stu-id="df000-213">Exception Types</span></span>](exception-handling/exception-types.md)|<span data-ttu-id="df000-214">Beschreibt die Ausnahmen, die Fehlerinformationen angeben.</span><span class="sxs-lookup"><span data-stu-id="df000-214">Describes exceptions, which specify error information.</span></span>|