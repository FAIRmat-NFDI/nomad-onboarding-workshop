<!-- ## Creating an Electronic Lab Notebook using Custom schema -->

# The Six Rules of Building a Custom ELN Schema

To build and customize your NOMAD ELN, you'll need to write code using the NOMAD metainfo schema language. However, don't be intimidated by the term "code"—this process requires only a basic understanding of programming and computer algorithms.
In this section, we’ll first outline the essential rules for writing a NOMAD ELN schema. Then, we'll guide you step-by-step as you put these principles into practice to create your first custom ELN in NOMAD. 

## **1- Schemas can be Written in YAML Language**

NOMAD schemas can be created with your favorite text editor using the YAML language and saved in the NOMAD **archive.yaml** format.

YAML, short for "YAML Ain't Markup Language," is a lightweight and human-readable data serialization language. It is a way to represent data in a structured format that's both easy for humans to read and write, and for machines to parse and process. It uses indentation and whitespace to organize data.

??? note "What is a serialization language?"

    A serialization language is a way to convert complex data structures, like objects or lists, into a simple format that can be easily stored or transmitted. This format can then be used to recreate the original data structure later. Common examples include JSON, XML, and YAML, which turn data into a text format that can be shared between different systems or saved for later use.

NOMAD's archive.yaml files start with the `definitions` keyword and can have a `name` and `description`.


```yaml
definitions:
  name: My NOMAD ELN
  description: This is an electronic lab notebook schema that includes several sections.
```


## **2- Sections Must be Defined**
The building blocks of a schema are sections. They are a representation of data and they are the objects that can be instantiated in NOMAD to build your ELN. 
Sections must be defined with a name, a set of quantities, and instructions on how they should be handled. 

??? note "What is meant by instantiation?"

    "Instantiated" means creating a specific instance of something based on a general definition or template. For example, in programming or data management, if you have a general template (like a class or section), instantiating it means creating a real, usable object or entity from that template with specific values or attributes.

Sections can be defined by using the keyword `sections` and the name of the section with a single indentation.

```yaml
definitions:
  name: My NOMAD ELN
  description: This is an electronic lab notebook schema that includes several sections.

  sections:
    My_first_section:
    My_second_section:
    My_third_section:
```

## **3- Sections Can Inherit from Other Sections**
Sections can also borrow the structure of other sections. This is called inherintance. 
This is useful because NOMAD offers several built-in objects called `base-sections`, which can help you write your schema efficiently.

The built-in base-sections can be inhereted to a user defined section using the `base-section` keyword, and then listing address of the base sections with a single indentation.

```yaml
definitions:
  name: My NOMAD ELN
  description: This is an electronic lab notebook schema that includes several sections.

  sections:
    My_first_section:
        base-sections:
            - nomad.datamodel.data.EntryData
```
## **4- Sections Contain Quantities and Other Sections (Sub-Sections)**
Each section contains a set of quantites that need to be captured by the ELN. The quantities represent the parameters of your measurement or processing conditions.
In addition, sections can also include sub-sections, which can be instantiated within the NOMAD dashboard of the relevant section.

```yaml
definitions:
  name: My NOMAD ELN
  description: This is an electronic lab notebook schema that includes several sections.

  sections:
    My_first_section:
        base-sections:
            - nomad.datamodel.data.EntryData
        quantities:

        sub-sections:
```

## **5- Quantities are Defined with Properties**

Quantities define possible primitive values. The first line in the quantity definition includes a user-defined name for the quantitiy. The basic properties that go into a quantity definition are `type`, `shape`, and `unit`.

```yaml
definitions:
  name: My NOMAD ELN
  description: This is an electronic lab notebook schema that includes several sections.

  sections:
    My_first_section:
        quantities:
            first_quantity:
                - type: #For example, str or np.float64
                - shape: #For example scalar or list (['*'])
                - unit: #For example, meters, amperes, or seconds
```

## **6- Section and Quantities Can Have Annotations**
 Annotations provide additional information that NOMAD can use to alter its behavior around these definitions and how users can interact with them. Annotations are named blocks of key-value pairs

```yaml
definitions:
  name: My NOMAD ELN
  description: This is an electronic lab notebook schema that includes several sections.

  sections:
    My_first_section:
      m_annotations:
        annotation_name:
          key1: value
          key2: value

        quantities:
            first_quantity:
                type: value
                shape: value
                unit: value
                m_annotations:
                    annotation_name:
                        key1: value
```



