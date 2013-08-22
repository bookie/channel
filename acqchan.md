# Acquisition Channel

```dot

```

## Declaration
```c

struct acq_channel
{
};

unsigned acqchan_init(unsigned chansize);
struct acq_channel *acqchan_deploy(struct sv_ctrl *svctrl);
void acqchan_kill(struct acq_channel *acqchan);

void acqchan_gc(void);

```
