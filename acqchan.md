# Acquisition Channel

```dot

```

## Declaration
```c

struct acq_channel
{
};

struct acq_channel *acqchan_deploy(struct sv_ctrl *svctrl);
void acqchan_kill(struct sv_ctrl *svctrl);

void acqchan_gc(void);

```
