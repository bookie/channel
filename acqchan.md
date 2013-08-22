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

/**
 * Number of acquisition channel in use.
 */
unsigned acqchan_occupied(void);

/**
 * Constraint the number of maximum usable acquisition channel.
 */
void acqchan_resize(unsigned size);

void acqchan_gc(void);

```
