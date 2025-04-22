# props

아래처럼, 스타일을 props로 받을 수 있고, ... 스프레드 연산자로 모든 props를 받아서
onpress같은 것들을 인터페이스에 선언안해도 받을 수 있다.

```tsx
interface CustomButtonProps extends PressableProps {
  label: string;
  size?: "small" | "medium" | "large";
  variant?: "filled";
}

function CustomButton({
  label,
  size = "large", // 기본값 설정
  variant = "filled",
  ...props
}: CustomButtonProps) {
  return (
    <Pressable
      style={({ pressed }) => [
        styles.container,
        styles[size],
        styles[variant],
        pressed ? styles.pressed : null,
      ]}
      {...props}
    >
      <Text style={styles[variant]}>{label}</Text>
    </Pressable>
  );
}

const styles = StyleSheet.create({
  container: {
    borderRadius: 8,
    justifyContent: "center",
    alignItems: "center",
  },
  medium: {
    width: "100%",
    height: 44,
  },
  large: {
    width: "100%",
    height: 44,
  },
  small: {
    width: "100%",
    height: 44,
  },
  filled: {
    backgroundColor: colors.ORANGE_600,
    fontSize: 14,
    fontWeight: "bold",
    color: colors.WHITE,
  },
  pressed: {
    opacity: 0.75,
  },
});

export default CustomButton;
```
