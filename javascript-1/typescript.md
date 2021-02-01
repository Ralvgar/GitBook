# Typescript

TypeScript is an open-source language which builds on JavaScript, by adding static type definitions.

Types provide a way to describe the shape of an object, providing better documentation, and allowing TypeScript to validate that your code is working correctly.

The benefits of TypeScript include −

* **Compilation** − JavaScript is an interpreted language. Hence, it needs to be run to test that it is valid. It means you write all the codes just to find no output, in case there is an error. Hence, you have to spend hours trying to find bugs in the code. The TypeScript transpiler provides the error-checking feature. TypeScript will compile the code and generate compilation errors, if it finds some sort of syntax errors. This helps to highlight errors before the script is run.
* **Strong Static Typing** − JavaScript is not strongly typed. TypeScript comes with an optional static typing and type inference system through the TLS \(TypeScript Language Service\). The type of a variable, declared with no type, may be inferred by the TLS based on its value.
* TypeScript **supports type definitions** for existing JavaScript libraries. TypeScript Definition file \(with **.d.ts** extension\) provides definition for external JavaScript libraries. Hence, TypeScript code can contain these libraries.
* TypeScript **supports Object Oriented Programming** concepts like classes, interfaces, inheritance, etc.

Some examples from my code:

```javascript

///
interface Props {
  text: string;
  date?: string;
  onDateChanged: (value: string) => void;
}

///
interface Props {
  value: string;
  icon: Icon;
}

export const IconWithValue: FunctionComponent<Props> = ({ value, icon }) => {
  return (
    <p className="icon-elem">
      <FontAwesomeIcon icon={getIconFromIconName(icon)} size="lg" />{" "}
      <span className="value-elem">{value}</span>
    </p>
  );
};

///
const [humidityData, setHumidityData] = useState<ApiResponse[]>();

///
onDateChanged={(value: string) => setToDate(value)}

//
export enum Icon {
  thermometer,
  humidity,
}

//
export enum HistoryGraphConfig {
  endTimeValue = 10,
  marginY = 20,
  marginX = 55,
  bottomAxisNumTicks = 5,
  height = 118,
}
```

{% embed url="https://www.typescriptlang.org/docs/handbook/intro.html" %}



